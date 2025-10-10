---
title: OWASP Top 10 - 2021
date modified: Monday, May 27th 2024, 3:28:59 pm
---
## OWASP Top 10 (2021):

*Note that this is part of my [[Web Application Hacking Methodology]].*

1. [Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
	1. This refers to services implementing poor access control and enabling users to access data/content outside of their intended permissions.
	2. Common CWEs include:
		1. [*CWE-200: Exposure of Sensitive Information to an Unauthorized Actor*](https://cwe.mitre.org/data/definitions/200.html)
		2. [*CWE-201: Insertion of Sensitive Information Into Sent Data*](https://cwe.mitre.org/data/definitions/201.html)
		3. [*CWE-352: Cross-Site Request Forgery (CSRF)*](https://cwe.mitre.org/data/definitions/352.html)
	3. The possible impacts of this are:
		1. Unauthorized data disclosure, modification or partial/full destruction of data.
2. [Cryptographic Failures](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)
	1. This refers to weak or lack of cryptographic measures in place. This frequently enables users to gain access to sensitive data.
	2. Common CWEs include:
		1. [*CWE-259: Use of Hard-coded Password*](https://cwe.mitre.org/data/definitions/259.html)
		2. [_CWE-327: Broken or Risky Crypto Algorithm_ ](https://cwe.mitre.org/data/definitions/327.html)
		3. [_CWE-331 Insufficient Entropy_ ](https://cwe.mitre.org/data/definitions/331.html)
	3. The possible impacts are:
		1. Exposure of sensitive data, such as PII, financial records or medical records.
3. [Injection](https://owasp.org/Top10/A03_2021-Injection/)
	1. This refers to applications that are vulnerable to some kind of code injection.
	2. Common CWEs include:
		1. [_CWE-79: Cross-site Scripting_ ](https://cwe.mitre.org/data/definitions/79.html)
		2. [_CWE-89: SQL Injection_ ](https://cwe.mitre.org/data/definitions/89.html)
		3. [_CWE-73: External Control of File Name or Path_ ](https://cwe.mitre.org/data/definitions/73.html)
	3. The possible impacts are:
		1. Exposure of sensitive data, such as PII, financial records or medical records.
		2. Authentication Bypass
		3. Privilege Escalation
		4. In severe cases, RCE
		5. Unauthorized data disclosure, modification or partial/full destruction of data.
4. [Insecure Design](https://owasp.org/Top10/A04_2021-Insecure_Design/)
	1. This refers to the fact that code isn't being designed with security in mind in the beginning and security is being shoehorned in at the end.
		1. It also can be described as: "missing or ineffective control design."
	2. Common CWEs include:
		1. [_CWE-209: Generation of Error Message Containing Sensitive Information_](https://cwe.mitre.org/data/definitions/209.html)
		2. [_CWE-256: Plaintext Storage of a Password_](https://cwe.mitre.org/data/definitions/256.html)
		3. [_CWE-501: Trust Boundary Violation_](https://cwe.mitre.org/data/definitions/501.html)
		4. [_CWE-522: Insufficiently Protected Credentials_](https://cwe.mitre.org/data/definitions/522.html)
	3. The possible impacts are:
		1. Privilege Escalation
		2. Sensitive data exposure, such as credentials or user data.
		3. Authentication Bypass
5. [Security Misconfiguration](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/)
	1. This refers to applications that are misconfigured and have not been hardened.
	2. Common CWEs include:
		1. [_CWE-16 Configuration_ ](https://cwe.mitre.org/data/definitions/16.html)
		2. [_CWE-611 Improper Restriction of XML External Entity Reference_](https://cwe.mitre.org/data/definitions/611.html)
	3. The possible impacts are:
		1. Unauthorized Access
		2. Data Exposure
		3. RCEs
		4. System compromise
6. [Vulnerable and Outdated Components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)
	1. This refers to web applications not using up to date software and components that have proven to be vulnerable.
	2. Common CWEs include are:
		1. [_CWE-1104: Use of Unmaintained Third-Party Components_ ](https://cwe.mitre.org/data/definitions/1104.html)
	3. The possible impacts are:
		1. Compliance Violation
		2. Low hanging fruit exploitation
		3. Other listed impacts, Data exposures, sensitive data leaks, etc
7. [Identification and Authentication Failures](https://owasp.org/Top10/A07_2021-Identification_and_Authentication_Failures/)
	 1. Also known as "Broken Authentication" this refers to user authentication/session management not being sufficient and complete enough, so it can be bypassed.
	 2. Common CWEs include:
		 1. _[CWE-297: Improper Validation of Certificate with Host Mismatch](https://cwe.mitre.org/data/definitions/297.html)
		 2. [_CWE-287: Improper Authentication_](https://cwe.mitre.org/data/definitions/287.html)
		 3. [_CWE-384: Session Fixation_](https://cwe.mitre.org/data/definitions/384.html)
	3. The possible impacts are:
		1. Account compromise
		2. Denial of device
		3. Botting
		4. Credential Stuffing
8. [Software and Data Integrity Failures](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/)
	1. This refers to making assumptions with software updates, critical data and CI/CD pipelines without verification.
	2. Common CWEs Include:
		1. [_CWE-829: Inclusion of Functionality from Untrusted Control Sphere_ ](https://cwe.mitre.org/data/definitions/829.html)
		2. [_CWE-494: Download of Code Without Integrity Check_](https://cwe.mitre.org/data/definitions/494.html)
		3. [_CWE-502: Deserialization of Untrusted Data_](https://cwe.mitre.org/data/definitions/502.html)
	3. The possible impacts are:
		1. Low hanging fruit exploits
		2. Authentication bypass
		3. sensitive data exposure.
9. [Security Logging and Monitoring Failures](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)
	1. This refers to bad practices that are found within logging and monitoring features of web apps.
	2. Common CWEs include:
		1. _CWE-778 Insufficient Logging_
		2. _CWE-117 Improper Output Neutralization for Logs_
		3. _CWE-223 Omission of Security-relevant Information_
		4. _CWE-532_ _Insertion of Sensitive Information into Log File_
	3. The impacts of this are:
		1. Privilege Escalation
		2. Sensitive data exposure
10. [Server-Side Request Forgery (SSRF)](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/)
	1. This refers to when attackers are able to craft malicious inputs to the server that cause unintended processes to occur.
	2. Common CWEs include:
		1. [CWE-918: Server-Side Request Forgery (SSRF)](https://cwe.mitre.org/data/definitions/918.html)
	3. The impacts of this are:
		1. Internal network access
		2. Data exfiltration
		3. External service abuse.