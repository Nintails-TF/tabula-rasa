---
date created: Thursday, March 26th 2026, 1:45:43 pm
date modified: Thursday, March 26th 2026, 2:03:32 pm
Gen: "1"
---

# Week 20-21 - Further on OpenStack (Orchestration & Autoscaling):

# 1. Introduction:

In the previous part we looked at a broad range of aspects around OpenStack and focused on the practical aspects of running a VM. This part focuses on a more advanced aspect called **autoscaling** and the concepts and techniques behind it.

First we look at how autoscaling is supported in OpenStack by an approach to managing resources called **orchestration**, and the specific means of orchestrating resources using what is called a **"stack"** written in the YAML language. The templates use the Heat Orchestration Template (HOT) specification.

To reach the autoscaling example, we first outline the format and operation of orchestration specifications, then run through a smaller example that simply starts a single VM instance, before implementing autoscaling on OpenStack.

---

# 2. Aims:

**After studying this part you should be able to:**

- Understand the operation of stacks in OpenStack and how they can be used to deploy and configure resources (a process known as "orchestration")
- Deploy "autoscaling" stacks where resources are scaled by the system to meet demand
- Explain some of the resources that stacks may include (health monitors, alarms, scaling policies, etc.)

---

# 3. OpenStack Orchestration:

Orchestration in cloud terms is a means to create a set of cloud components (networks, VMs, storage, etc.) automatically in one simple action. Instead of manually creating a network, then a VM, then allocating a floating IP address, you write a specification of what components are required and invoke the specification to create all components as one automated sequence.

The main OpenStack orchestration project is called **HEAT**, which has developed a standard way of orchestrating resources using descriptions called **"templates"**. HEAT Orchestration Templates (HOTs) have a fixed structure and are written using the YAML language.

## 3.1. Template Structure:

The structure of a HOT template is as follows (lines starting with `#` are comments):

```yaml
heat_template_version: 2021-04-16
description:
  # a description of the template
parameter_groups:
  # a declaration of input parameter groups and order
parameters:
  # declaration of input parameters
resources:
  # declaration of template resources
outputs:
  # declaration of output parameters
```

**Section descriptions:**

- **heat_template_version:** Tells the system what version and functions can be found in the template. Different standards are associated with different dates
- **description:** Human-readable description of what the template does (optional but good practice, intended to build a repository of templates)
- **parameter_groups:** Allows parameters to be grouped and ordered — e.g. a login username and password can be grouped so it's obvious they are associated. This allows a client interface to display them logically
- **parameters:** Inputs to the template provided when invoking it (like parameters passed into a function). Can have default values used if no value is provided
- **resources:** Specifies what OpenStack resources should be created (instances, networks, routers, etc.)
- **outputs:** Parameters returned by the template after creation (optional)

Some sections relate to presenting the template as a form in a web page where parameters can be listed with fields pre-filled with default values. When running, the template can return information to display, such as a VM's IP address.

## 3.2. Simple Template Example:

A very short template to deploy a single compute instance:

```yaml
heat_template_version: 2021-04-16
description: Simple template to deploy a single compute instance
resources:
  my_instance:
    type: OS::Nova::Server
    properties:
      image: ExampleWebApp
      flavor: m1.small
      network: private
```

The resource is named `my_instance`, of type `OS::Nova::Server`. It uses the image `ExampleWebApp`, flavor `m1.small`, and runs on the network named `private`. The named items (image, flavor, network) must exist in the OpenStack installation for the template to run successfully.

## 3.3. Parameterised Templates:

Normally templates are more generally applicable, so elements are passed as parameters with default values:

```yaml
heat_template_version: 2021-04-16
description: Simple template to deploy a single compute instance
parameters:
  image:
    type: string
    label: Image name
    description: Name of the image to start
    default: ExampleWebApp
  flavor:
    type: string
    label: Flavor
    description: Name of the flavour to use for instance
    default: m1.small
  network:
    type: string
    label: Private network
    description: Name or ID of private network
    default: private
resources:
  my_instance:
    type: OS::Nova::Server
    properties:
      image: { get_param: image }
      flavor: { get_param: flavor }
      networks:
        - network: { get_param: network }
```

The `get_param` template function retrieves the specific parameter value. When the template is called, an image name and flavor can be specified; if not, defaults are used.

## 3.4. Environment Files:

HEAT allows **environment files** used in conjunction with templates to specify parameter values. The template can have parameter defaults removed and paired with a separate environment file:

```yaml
parameter_defaults:
  image: ExampleWebApp
  flavor: m1.small
  network: private
```

This means the template can be used with any image, flavor or network — only the environment file needs changing.

**Important:** When editing YAML, avoid introducing non-printing characters. Problems with tabs have been observed — use a simple text editor like Notepad.

---

# 4. Autoscaling Background:

## 4.1. Why Autoscaling Matters:

A real-world example: during the 2016 UK referendum, the online voter registration website crashed due to a surge of traffic after politicians emphasised the importance of registering. Emergency legislation extended the deadline by 24 hours. This is an example of IT infrastructure failure due to workload pressure.

**Technical causes of such failures:**

- Increasing workload raises response times until the HTTP request-response cycle breaks — the server may eventually reply, but the client browser has already timed out and reported an error (sometimes inaccurately, e.g. "server not found")
- Database write operations can timeout under volume pressure
- Applications that need to allocate real memory can throw errors and fail if memory isn't available when requested

## 4.2. Scaling Approaches:

When a web server comes under increasing load, its response time degrades. Before it becomes critical, more resources should be brought online to service demand and maintain quality of service.

**Vertical scaling:** Adding more power to the server machine (more CPUs, more memory). Drawbacks include needing to stop and reconfigure the machine, and hard limits to how far it can be extended.

**Horizontal scaling:** Adding another machine and sharing the load between existing and new servers. This is the approach examined in this part.

Previously, organisations were sometimes reluctant to have standby resources with little normal justification, accepting that infrastructure might fail under extraordinary circumstances. Today the climate has changed — more users on the web are more demanding, and if a website fails they go elsewhere. Cloud resources and the "pay for use" model can restrict the cost of having sizable infrastructure on call.

---

# 5. A Web Application with Load Balancing:

## 5.1. Basic Architecture Problem:

In a basic web application, all requests arrive at a single web server via a single static IP address. As requests rise, the server slows. Adding memory or a CPU means shutting it down, and adding another machine is problematic because all requests go directly to the existing server.

The solution is to introduce a **load balancer (LB)** that takes the place of the server in receiving incoming requests, then distributes them to multiple servers.

## 5.2. OpenStack LBaaS Architecture:

OpenStack provides **Load Balancer as a Service (LBaaS)** with the following components:

- **Load balancer:** Has a floating IP address to receive incoming requests
- **Listeners:** Handle specific requests using different protocols or ports (e.g. HTTP on port 80, HTTPS on port 443)
- **Pool:** Groups a set of one or more member VMs together that can respond to requests
- **Health monitor:** Monitors the pool of VMs and ensures requests are not sent to VMs that are not responding

## 5.3. Load Balancer Considerations:

### Session Maintenance:

When a request arrives, the LB routes it to one server. If the LB receives further requests from the same client, it must pass them to the same server, which may have retained session information (e.g. login credentials). Other servers won't have this information and would deny access.

### Server Failure:

OpenStack uses a **health monitor** to monitor all VMs grouped in a pool. When a new VM starts, it's added to the pool and automatically monitored. If a health monitor finds an instance is not running, it removes it.

**Health monitor specification:**

```yaml
lb_monitor:
  type: OS::Octavia::HealthMonitor
  properties:
    type: TCP
    delay: 5
    max_retries: 3
    timeout: 4
    admin_state_up: true
    pool: { get_resource: pool }
```

This monitor uses TCP, connecting every 5 seconds, allowing 4 seconds to establish a connection, with up to 3 attempts before declaring failure. The monitor's properties include the protocol type, time between messages (delay), number of connection attempts (max_retries), and connection timeout.

### Load Balancing Algorithms:

With multiple servers, the LB needs to decide which server receives the next request. Available algorithms in OpenStack:

- **ROUND_ROBIN:** Picks each server in turn (A → B → C → A → ...). Problem: one request may take considerably longer than another
- **LEAST_CONNECTIONS:** Samples the load on each server and selects the least loaded. More sophisticated but incurs overhead in assessing server load
- **SOURCE_IP:** Generates VM selection based on the client's IP, meaning it always talks to the same VM even outside a normal session

## 5.4. Load Balancer Template:

```yaml
lb:
  type: OS::Octavia::LoadBalancer
  properties:
    vip_subnet: { get_param: subnet_id }

lb_floating:
  type: "OS::Neutron::FloatingIP"
  properties:
    floating_network_id: { get_param: external_network_id }
    port_id: { get_attr: [lb, vip_port_id] }
```

The balancer is associated with a subnet where the pool of VMs will run and assigned a Virtual IP (VIP) address. A floating IP on the external network is assigned to the load balancer's VIP port.

**Pool specification:**

```yaml
pool:
  type: OS::Octavia::Pool
  properties:
    protocol: TCP
    lb_algorithm: ROUND_ROBIN
    listener: { get_resource: listener }
```

**Listener specification:**

```yaml
listener:
  type: OS::Octavia::Listener
  properties:
    loadbalancer: { get_resource: lb }
    protocol: TCP
    protocol_port: 22
```

## 5.5. Autoscaling Components:

While OpenStack collects data about VM loads (CPU, memory, etc.) for billing and autoscaling, two additional items are needed for autoscaling: **alarms** and **scaling policies**.

### Scaling Policy:

A scaling policy specifies what action to take when an alarm fires.

```yaml
web_server_scaleup_policy:
  type: OS::Heat::ScalingPolicy
  properties:
    adjustment_type: change_in_capacity
    auto_scaling_group_id: { get_resource: asg }
    cooldown: 60
    scaling_adjustment: 1
```

This policy adds one instance to the autoscaling group. The **cooldown period** (60 seconds) is the time that must pass before the alarm can fire again — this prevents multiple signals from the same alarm prompting several instances to launch. The cooldown period should be longer than the time for a new instance to come online.

### Alarm:

An alarm regularly assesses monitoring data against a set of criteria. When the criteria are met, it triggers and applies a scaling policy.

```yaml
cpu_alarm_high:
  type: OS::Aodh::GnocchiAggregationByResourcesAlarm
  properties:
    description: Scale up if CPU > 50% for 1 minute
    metric: cpu_util
    aggregation_method: mean
    granularity: 60
    evaluation_periods: 1
    threshold: 50
    resource_type: instance
    comparison_operator: gt
    alarm_actions:
      - str_replace:
          template: trust+url
          params:
            url: { get_attr: [web_server_scaleup_policy, signal_url] }
    query:
      list_join:
        - ''
        - - {'=': {server_group: {get_param: "OS::stack_id"}}}
```

This alarm is set on `cpu_util` and fires when CPU reaches 50%. The **granularity** property (60 seconds) specifies how long the CPU must remain above 50% before the alarm triggers. OpenStack's data collection ("archiving") currently operates at a low level — every 5 minutes over 30 days — so when alarm conditions are met, there may be a several-minute wait for the alarm state to actually change.

The alarm action is a URL pointing to the scale-up policy declaration. The query restricts data to contain only this stack's ID (a unique identifier).

### Autoscaling Group:

The autoscaling group is the most significant resource, defining what to scale and the pool boundaries:

```yaml
asg:
  type: OS::Heat::AutoScalingGroup
  properties:
    min_size: 1
    max_size: 2
    resource:
      properties:
        flavor: { get_param: flavor }
        image: { get_param: image }
        metadata:
          metering.server.group: { get_param: 'OS::stack_id' }
        network: { get_param: subnet_network_id }
        pool_id: { get_resource: pool }
        subnet: { get_param: subnet_id }
      type: http://137.108.95.253/lb.yaml
```

Key parts: it defines the **item to be scaled** (the resource — referencing another YAML file specifying the VM server instance), and the **minimum and maximum size** of the pool. Parameters are passed down to the referenced file relating to running the instance (flavor, etc.) and the enclosing stack ID.

---

# 6. Summary:

In this part you have seen how orchestration in OpenStack operates and gained practical experience using this approach to automate the deployment of autoscaled resources.

**Key concepts covered:**

- **Orchestration** automates creation of cloud components (networks, VMs, storage) in one action using HEAT templates written in YAML
- **Templates** have a fixed structure with sections for version, description, parameter groups, parameters, resources and outputs
- **Environment files** allow templates to be reused with different parameter values
- **Autoscaling** dynamically adds or removes resources in response to demand, using horizontal scaling with load balancing
- **LBaaS (Load Balancer as a Service)** provides load balancer, listeners, pools and health monitors
- **Health monitors** track VM availability and remove unresponsive instances from the pool
- **Scaling policies** define what action to take (e.g. add one instance) with cooldown periods to prevent over-scaling
- **Alarms** (using Aodh/Gnocchi) assess monitoring data against criteria (e.g. CPU > 50%) and trigger scaling policies when conditions are met
- **Autoscaling groups** define the resource to scale and minimum/maximum pool size

---