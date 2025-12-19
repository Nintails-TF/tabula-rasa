---
date created: Friday, November 14th 2025, 2:31:31 pm
date modified: Friday, November 14th 2025, 2:36:33 pm
---

# TM352 Block 1 Part 4: Services

## Overview

This module covers the foundations of connecting to backend services and securing those connections in web applications.
## Core Topics

### 1. Connecting Services

#### Application Programming Interfaces (APIs)

An API is a contract between server and client that specifies:
- **Transmission technology** - How data is sent over the network
- **Endpoints** - What functionality the server offers (typically URLs)
- **Inputs** - Required and optional data for each endpoint
- **Outputs** - Server responses and error messages

**Key Benefits:**
- Clear definition of server functionality
- Decoupling between client and server implementations
- Single API can serve multiple client types (web, mobile)
- Maintenance flexibility

#### Transmission Technologies

**REST (REpresentational State Transfer)**
- Architectural style, not a standard
- Uses HTTP verbs (GET, POST, PUT, PATCH, DELETE)
- URL-based endpoints
- Stateless - server retains no client state
- Supports caching and load balancing

|Verb|Collection Endpoint|Item Endpoint|
|---|---|---|
|GET|Fetch all items|Fetch single item|
|POST|Create new item|Unused|
|PUT/PATCH|Unused|Update item|
|DELETE|Delete all items|Delete single item|

**SOAP (Simple Object Access Protocol)**
- XML-based RPC protocol
- Can use various transport protocols
- Single URL endpoint
- Function specified in message body

**gRPC**
- Modern RPC protocol
- Uses Protocol Buffers for serialization
- High performance
- Cannot be used directly in browsers

#### Data Transfer Formats

**JSON (JavaScript Object Notation)**

```json
{
  "id": 4323,
  "title": "A playlist",
  "songs": [
    {
      "id": 937293,
      "title": "The greatest song ever"
    }
  ]
}
```

**XML**

```xml
<playlist>
  <id>4323</id>
  <title>A playlist</title>
  <songs>
    <song>
      <id>937293</id>
      <title>The greatest song ever</title>
    </song>
  </songs>
</playlist>
```

**YAML**

```yaml
id: 4323
title: A playlist
songs:
  - id: 937293
    title: The greatest song ever
```

### 2. Security

#### Cryptography

**Symmetric Encryption**
- Same key for encryption and decryption
- Key exchange problem
- More efficient than asymmetric

![[../../../../03_Reference/Pictures/week4-tm352-symmetric-encryption.png]]

**Asymmetric Encryption**
- Public/private key pairs
- Public key encrypts, private key decrypts
- Solves key exchange problem
- Less efficient than symmetric
![[../../../../03_Reference/Pictures/week4-tm352-asymmetric-encryption.png]]

**Key Exchange (Diffie-Hellman)**
- Creates shared secret without transmitting it
- Combines asymmetric and symmetric benefits
![[../../../../03_Reference/Pictures/week4-tm352-diffie-hellman-key-exchange.png]]

**Transport Layer Security (TLS)**
1. Client connects and shares supported algorithms
2. Server picks compatible algorithm
3. Server sends certificate
4. Client verifies certificate via Certificate Authority
5. Key exchange process
6. Secure communication established

#### Authentication

**Bearer Tokens**
- Replace username/password after initial auth
- Stateless authentication for REST APIs
- Must be transmitted securely

**JSON Web Tokens (JWT)**

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiI4MzkyNzQiLCJuYW1lIjoiU3VwZXIgQWRtaW4iLCJpYXQiOjE1MTYyMzkwMjIsInJvbGVzIjpbImFkbWluIl19.
iNCueJNshk75SImlwz88XwcVnwhi4Zxcm7k1SKiT7Q
```

Structure:
- **Header**: Algorithm and token type
- **Payload**: User data and claims
- **Signature**: Verification hash

**OAuth 2.0 & OpenID Connect**
- OAuth 2.0: Authorization protocol
- OpenID Connect: Authentication layer on OAuth 2.0
- Separates auth from main application

**Multi-Factor Authentication**
- Knowledge: Something you know (password)
- Ownership: Something you have (token, phone)
- Inherence: Something you are (biometrics)

#### Data Validation

**Validation Types:**
- **Data type** - Correct type (string, number, etc.)
- **Value range** - Within allowed bounds
- **Patterns** - Matches specific format (email, etc.)
- **Allowed values** - From predefined list
- **Empty** - Whether empty values allowed
- **Optional** - Whether field required
- **Custom** - Complex validation logic

**Cross-Site Request Forgery (XSRF/CSRF) Protection**
- Attacker tricks user into making unwanted requests
- Solution: Include random token in forms
- Server validates token matches cookie value

## Key Takeaways
1. **APIs provide structured communication** between clients and servers
2. **REST is dominant** for web applications due to HTTP alignment
3. **JSON is preferred** for web data transfer
4. **TLS is essential** for secure communication
5. **JWTs enable stateless authentication** for REST APIs
6. **Multi-factor authentication** significantly improves security
7. **Data validation** must occur server-side
8. **XSRF protection** requires token validation