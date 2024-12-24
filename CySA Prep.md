### 1.0 Security Operations
#### 1.1 Explain the importance of system and network architecture concepts in security operations.
- **Log ingestion**
  - Time synchronization
  - Logging levels
- **Operating system (OS) concepts**
  - Windows Registry
  - System hardening
  - File structure
    - Configuration file locations
  - System processes
  - Hardware architecture
- **Infrastructure concepts**
  - Serverless
  - Virtualization
  - Containerization
- **Network architecture**
  - On-premises
  - Cloud
  - Hybrid
  - Network segmentation
  - Zero trust
  - Secure Access Secure Edge (SASE)
  - Software-defined networking (SDN)
- **Identity and access management**
  - Multifactor authentication (MFA)
  - Single sign-on (SSO)
  - Federation
  - Privileged access management (PAM)
  - Passwordless
  - Cloud access security broker (CASB)
- **Encryption**
  - Public Key Infrastructure (PKI)
  - Secure Sockets Layer (SSL) inspection
- **Sensitive data protection**
  - Data loss prevention (DLP)
  - Personally Identifiable Information (PII)
  - Cardholder Data (CHD)

#### 1.2 Given a scenario, analyze indicators of potentially malicious activity.
- **Network-related**
  - Bandwidth consumption
  - Beaconing
  - Irregular peer-to-peer communication
  - Rogue devices on the network
  - Scans/sweeps
  - Unusual traffic spikes
  - Activity on unexpected ports
- **Host-related**
  - Processor consumption
  - Memory consumption
  - Drive capacity consumption
  - Unauthorized software
  - Malicious processes
  - Unauthorized changes
  - Unauthorized privileges
  - Data exfiltration
  - Abnormal OS process behavior
  - File system changes or anomalies
  - Registry changes or anomalies
  - Unauthorized scheduled tasks
- **Application-related**
  - Anomalous activity
  - Introduction of new accounts
  - Unexpected output
  - Unexpected outbound communication
  - Service interruption
  - Application logs
- **Other**
  - Social engineering attacks
  - Obfuscated links

#### 1.3 Given a scenario, use appropriate tools or techniques to determine malicious activity.
- **Tools**
  - Packet capture (e.g., Wireshark, tcpdump)
  - Log analysis/correlation (e.g., SIEM, SOAR)
  - Endpoint security (e.g., EDR)
  - DNS and IP reputation (e.g., WHOIS, AbuseIPDB)
  - File analysis (e.g., Strings, VirusTotal)
  - Sandboxing (e.g., Joe Sandbox, Cuckoo Sandbox)
- **Common techniques**
  - Pattern recognition (e.g., Command and control)
  - Interpreting suspicious commands
  - Email analysis (e.g., headers, impersonation)
  - File analysis (e.g., hashing)
  - User behavior analysis (e.g., abnormal account activity)

#### 1.4 Compare and contrast threat-intelligence and threat-hunting concepts.
- **Threat actors**
  - Advanced Persistent Threat (APT)
  - Hacktivists
  - Organized crime
  - Nation-state
  - Script kiddie
  - Insider threat (intentional/unintentional)
- **Tactics, techniques, and procedures (TTP)**
- **Collection methods and sources**
  - Open source (e.g., social media, CERT)
  - Closed source (e.g., paid feeds, internal sources)
- **Threat intelligence sharing**
  - Incident response
  - Vulnerability management

#### 1.5 Explain the importance of efficiency and process improvement in security operations.
- **Standardize processes**
  - Automation
- **Streamline operations**
  - Security Orchestration, Automation, and Response (SOAR)
- **Technology and tool integration**
  - APIs
  - Webhooks
- **Single pane of glass**

---
### 2.0 Vulnerability Management
#### 2.1 Given a scenario, implement vulnerability scanning methods and concepts.
- **Asset discovery**
  - Map scans
  - Device fingerprinting
- **Special considerations**
  - Scheduling
  - Operations
  - Performance
  - Sensitivity levels
  - Segmentation
  - Regulatory requirements
- **Internal vs. external scanning**
- **Agent vs. agentless**
- **Credentialed vs. non-credentialed**
- **Passive vs. active**
- **Static vs. dynamic**
  - Reverse engineering
  - Fuzzing
- **Critical infrastructure**
  - Operational Technology (OT)
  - Industrial Control Systems (ICS)
  - Supervisory Control and Data Acquisition (SCADA)
- **Security baseline scanning**
- **Industry frameworks**
  - Payment Card Industry Data Security Standard (PCI DSS)
  - Center for Internet Security (CIS) benchmarks
  - Open Web Application Security Project (OWASP)
  - International Organization for Standardization (ISO) 27000 series

#### 2.2 Given a scenario, analyze output from vulnerability assessment tools.
- **Tools**
  - Network scanning and mapping (e.g., Angry IP Scanner, Maltego)
  - Web application scanners (e.g., Burp Suite, ZAP, Arachni, Nikto)
  - Vulnerability scanners (e.g., Nessus, OpenVAS)
  - Debuggers (e.g., Immunity Debugger, GNU Debugger (GDB))
  - Multipurpose tools (e.g., Nmap, Metasploit Framework (MSF), Recon-ng)
  - Cloud infrastructure assessment tools (e.g., Scout Suite, Prowler, Pacu)

#### 2.3 Given a scenario, analyze data to prioritize vulnerabilities.
- **Common Vulnerability Scoring System (CVSS) interpretation**
  - Attack vectors
  - Attack complexity
  - Privileges required
  - User interaction
  - Scope
  - Impact
    - Confidentiality
    - Integrity
    - Availability
- **Validation**
  - True/false positives
  - True/false negatives
- **Context awareness**
  - Internal
  - External
  - Isolated
- **Exploitability/weaponization**
- **Asset value**
- **Zero-day vulnerabilities**

#### 2.4 Given a scenario, recommend controls to mitigate attacks and software vulnerabilities.
- **Common vulnerabilities**
  - Cross-site scripting (XSS): reflected, persistent
  - Overflow vulnerabilities: buffer, integer, heap, stack
  - Data poisoning
  - Broken access control
  - Cryptographic failures
  - Injection flaws
  - Cross-site request forgery (CSRF)
  - Directory traversal
  - Insecure design
  - Security misconfiguration
  - End-of-life or outdated components
  - Identification and authentication failures
  - Server-side request forgery (SSRF)
  - Remote code execution (RCE)
  - Privilege escalation
  - Local File Inclusion (LFI) / Remote File Inclusion (RFI)
- **Compensating controls**
- **Control types**
  - Managerial
  - Operational
  - Technical
  - Preventative
  - Detective
  - Responsive
  - Corrective
- **Patching and configuration management**
  - Testing
  - Implementation
  - Rollback
  - Validation
- **Maintenance windows**
- **Exceptions**
- **Risk management principles**
  - Accept
  - Transfer
  - Avoid
  - Mitigate
- **Policies, governance, and service-level objectives (SLOs)**
- **Prioritization and escalation**
- **Attack surface management**
  - Edge discovery
  - Passive discovery
  - Security controls testing
  - Penetration testing and adversary emulation
  - Bug bounty programs
  - Attack surface reduction
- **Secure coding best practices**
  - Input validation
  - Output encoding
  - Session management
  - Authentication
  - Data protection
  - Parameterized queries
- **Secure software development life cycle (SDLC)**
- **Threat modeling**

#### 2.5 Explain concepts related to vulnerability response, handling, and management.
- Compensating control
- Control types
	- Managerial
	- Operational
	- Technical
	- Preventative
	- Detective
	- Responsive
	- Corrective
• Patching and configuration
management
- Testing
- Implementation
- Rollback
- Validation
• Maintenance windows
• Exceptions
• Risk management principles
- Accept
- Transfer
- Avoid
- Mitigate
• Policies, governance, and service-
level objectives (SLOs)
• Prioritization and escalation
• Attack surface management
- Edge discovery
- Passive discovery
- Security controls testing
- Penetration testing and
adversary emulation
- Bug bounty
- Attack surface reduction
• Secure coding best practices
- Input validation
- Output encoding
- Session management
- Authentication
- Data protection
- Parameterized queries
• Secure software development
life cycle (SDLC)
• Threat modeling
### 3.0 Incident Response and Management
#### 3.1 Explain concepts related to attack methodology frameworks.
- **Cyber kill chains**
- **Diamond Model of Intrusion Analysis**
- **MITRE ATT&CK framework**
- **Open Source Security Testing Methodology Manual (OSSTMM)**
- **OWASP Testing Guide**

#### 3.2 Given a scenario, perform incident response activities.
- **Detection and analysis**
  - Indicators of Compromise (IoC)
  - Evidence acquisition
    - Chain of custody
    - Validating data integrity
    - Preservation
    - Legal hold
  - Data and log analysis
- **Containment, eradication, and recovery**
  - Scope
  - Impact
  - Isolation
  - Remediation
  - Re-imaging
  - Compensating controls

#### 3.3 Explain the preparation and post-incident activity phases of the incident management lifecycle.
- **Preparation**
  - Incident response plan
  - Tools
  - Playbooks
  - Tabletop exercises
  - Training
  - Business continuity (BC) / Disaster recovery (DR)
- **Post-incident activity**
  - Forensic analysis
  - Root cause analysis
  - Lessons learned

---

### 4.0 Reporting and Communication
#### 4.1 Explain the importance of vulnerability management reporting and communication.
- **Vulnerability management reporting**
  - Vulnerabilities
  - Affected hosts
  - Risk score
  - Mitigation
  - Recurrence
  - Prioritization
- **Compliance reports**
- **Action plans**
  - Configuration management
  - Patching
  - Compensating controls
  - Awareness, education, and training
  - Changing business requirements
- **Inhibitors to remediation**
  - Memorandum of Understanding (MOU)
  - Service-level Agreement (SLA)
  - Organizational governance
  - Business process interruption
  - Degrading functionality
  - Legacy systems
  - Proprietary systems
- **Metrics and Key Performance Indicators (KPIs)**
  - Trends
  - Top 10 vulnerabilities
  - Critical vulnerabilities and zero-days
  - Service-level objectives (SLOs)
- **Stakeholder identification and communication**

#### 4.2 Explain the importance of incident response reporting and communication.
- **Stakeholder identification and communication**
- **Incident declaration and escalation**
- **Incident response reporting**
  - Executive summary
  - Who, what, when, where, and why
  - Recommendations
  - Timeline
  - Impact
  - Scope
  - Evidence
- **Communications**
  - Legal
  - Public relations
    - Customer communication
    - Media
  - Regulatory reporting
  - Law enforcement
- **Root cause analysis**
- **Lessons learned**
- **Metrics and KPIs**
  - Mean Time to Detect (MTTD)
  - Mean Time to Respond (MTTR)
  - Mean Time to Remediate (MTTR)
  - Alert volume

---

### Acronym List
- **ACL**: Access Control List
- **API**: Application Programming Interface
- **APT**: Advanced Persistent Threat
- **ARP**: Address Resolution Protocol
- **AV**: Antivirus
- **BC**: Business Continuity
- **BCP**: Business Continuity Plan
- **BGP**: Border Gateway Protocol
- **C2**: Command and Control
- **CA**: Certificate Authority
- **CASB**: Cloud Access Security Broker
- **CDN**: Content Delivery Network
- ... *(full list continues)*

---

### Suggested Hardware and Software
#### Hardware
- Workstations (or laptops) with the ability to run virtual machines (VMs)
- Firewalls
- IDS/IPS
- Servers

#### Software
- **Operating Systems**
  - Windows OS (e.g., Commando VM)
  - Linux OS (e.g., Kali)
- **SIEM Tools**
  - Splunk
  - ELK
  - Greylog
- **Packet Analysis**
  - tcpdump
  - Wireshark
- **Vulnerability Scanners**
  - Nessus
  - OpenVAS
- **Cloud Instances**
  - AWS
  - Azure
  - Google Cloud Platform (GCP)
