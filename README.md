# Cybersecurity Training Portfolio — Masar / National Cyber Security Center

This repository contains a selection of hands-on tasks, reports, labs, and final-project work completed during the **Masar cybersecurity training program** delivered through the **National Cyber Security Center**.

The training covered multiple cybersecurity domains, including:

- Penetration Testing
- Blue Team / Defensive Security
- Malware Analysis
- Governance, Risk, and Compliance (GRC)
- DevSecOps / SAST
- SIEM and Log Analysis
- Incident Response
- Threat Intelligence
- MITRE ATT&CK
- Business Impact Analysis
- Security Governance and Risk Management

This repository is intended to serve as a practical cybersecurity portfolio demonstrating technical work, documentation, analysis, and defensive security concepts covered during the training.

---

## Repository Structure

```text
.
├── Blue-Team/
│   ├── Lumma-Stealer/
│   │   ├── screenshots/
│   │   ├── Lumma_Stealer_Analysis.md
│   │   └── README.md
│   │
│   └── lazarus-group-ttp-analysis/
│       ├── Lazarus_Group_TTP_MITRE_ATTCK_Profile.md
│       └── README.md
│
├── DevSecOps/
│   └── Semgrep-SAST/
│       ├── screenshots/
│       ├── semgrep-sast.md
│       └── README.md
│
├── Final-Project/
│   ├── Final_Project_Report.pdf
│   └── README.md
│
├── GRC/
│   ├── bazaarjo-business-impact-analysis/
│   │   ├── BazaarJo_Business_Impact_Analysis.md
│   │   └── README.md
│   │
│   ├── bazaarjo-governance-compliance/
│   │   ├── BazaarJo_Governance_Compliance_Remediation.md
│   │   └── README.md
│   │
│   └── bazaarjo-risk-assessment/
│       ├── bazaarjo-risk-assessment.md
│       └── README.md
│
├── Malware-Analysis/
│   ├── images/
│   ├── yara/
│   ├── README.md
│   └── malware-analysis.md
│
└── Penetration-Testing/
    └── pWnOS/
        ├── screenshots/
        ├── Web_Sec_Report.md
        └── README.md
```

---

# Training Areas

## 1. Penetration Testing

The penetration-testing section contains practical offensive-security exercises performed in controlled lab environments.

Topics practiced include:

- Network and service enumeration
- Web application enumeration
- Vulnerability identification
- Exploitation using security testing tools
- Remote Command Execution validation
- Metasploit usage
- Proof-of-Concept documentation
- Security findings and technical reporting

### Example Project

**pWnOS Web Security Assessment**

A practical web-service assessment involving enumeration, discovery of the web application path, vulnerability analysis, exploitation, and proof-of-concept validation.

See:

`Penetration-Testing/pWnOS/`

---

## 2. Blue Team & Threat Intelligence

The Blue Team section focuses on understanding attacker behavior, threat intelligence, MITRE ATT&CK mapping, and defensive security analysis.

### Lumma Stealer Analysis

Research and analysis of **Lumma Stealer / LummaC2**, including:

- Malware behavior
- Delivery methods
- Execution techniques
- Persistence
- Credential theft
- Data collection
- Command and Control
- Exfiltration
- Indicators of Compromise
- Detection recommendations
- MITRE ATT&CK mapping

See:

`Blue-Team/Lumma-Stealer/`

### Lazarus Group TTP Analysis

Threat-intelligence research on **Lazarus Group (G0032)** comparing:

- Operation Dream Job
- 3CX Supply-Chain Compromise

The project includes:

- Campaign comparison
- TTP evolution
- ATT&CK technique mapping
- Impact-based scoring
- Indicators of Compromise
- Threat actor profiling

See:

`Blue-Team/lazarus-group-ttp-analysis/`

---

## 3. Malware Analysis

The malware-analysis section contains practical static and dynamic analysis work performed in a controlled environment.

Areas covered include:

- File and hash inspection
- Static analysis
- Dynamic behavior analysis
- Process monitoring
- Network traffic analysis
- Timeline reconstruction
- Indicator extraction
- YARA rule creation
- Malware behavior documentation

The repository includes screenshots, analysis evidence, and YARA-related work.

See:

`Malware-Analysis/`

---

## 4. DevSecOps / SAST

The DevSecOps section includes practical **Static Application Security Testing (SAST)** using **Semgrep**.

The work demonstrates:

- Static code analysis
- Security rule execution
- Identifying insecure code patterns
- Reviewing findings
- Secure development concepts
- Integrating security into the software-development lifecycle

See:

`DevSecOps/Semgrep-SAST/`

---

## 5. Governance, Risk, and Compliance

The GRC section contains multiple business-oriented cybersecurity exercises based on the fictional organization **BazaarJo**.

### Cybersecurity Risk Assessment

The risk-assessment task includes:

- Risk context
- Risk appetite
- Risk register
- Likelihood and impact analysis
- Risk prioritization
- Risk treatment
- Risk ownership
- KRIs
- Management reporting

See:

`GRC/bazaarjo-risk-assessment/`

### Business Impact Analysis

The Business Impact Analysis identifies critical business processes and defines:

- Business dependencies
- Financial impact
- Customer impact
- Regulatory impact
- Recovery Time Objectives (RTO)
- Recovery Point Objectives (RPO)
- Recovery priorities

See:

`GRC/bazaarjo-business-impact-analysis/`

### Governance & Compliance Remediation

This project focuses on organizational security governance, including:

- Segregation of Duties
- Breach-notification governance
- CISO accountability
- Vendor risk management
- Board-level risk appetite
- Data privacy governance
- Policy review
- Security reporting
- Remediation planning

See:

`GRC/bazaarjo-governance-compliance/`

---

## 6. Final Project

The final project brings together several areas covered throughout the training, including offensive and defensive security activities, monitoring, analysis, incident handling, and security hardening.

The final report documents practical work performed by the project team, including:

- Vulnerable environment preparation
- Attack simulation
- SIEM monitoring
- Log collection and analysis
- Incident detection
- Security remediation
- Vulnerability mitigation
- Secure remote connectivity
- Team collaboration

See:

`Final-Project/`

---

# Skills Demonstrated

This repository demonstrates practical exposure to:

### Offensive Security

- Penetration Testing
- Web Application Security
- Enumeration
- Vulnerability Assessment
- Metasploit
- Exploitation Validation
- Proof-of-Concept Reporting

### Defensive Security

- SIEM
- Splunk
- Log Analysis
- Incident Detection
- Incident Response
- Threat Hunting
- Security Monitoring
- Security Hardening

### Threat Intelligence

- MITRE ATT&CK
- TTP Analysis
- Threat Actor Profiling
- Malware Research
- Indicators of Compromise
- Attack Lifecycle Analysis

### Malware Analysis

- Static Analysis
- Dynamic Analysis
- Network Analysis
- Process Monitoring
- YARA
- Behavioral Analysis

### Governance & Risk

- Risk Assessment
- Risk Register Development
- Risk Treatment
- Business Impact Analysis
- RTO / RPO
- Cybersecurity Governance
- Compliance Gap Analysis
- Vendor Risk Management
- Security Reporting

### DevSecOps

- SAST
- Semgrep
- Secure SDLC
- Static Code Analysis
- Secure Code Review

---

# Tools and Technologies

Some of the tools and frameworks used throughout the training include:

- Kali Linux
- Metasploit Framework
- Nmap
- Splunk
- Wireshark
- YARA
- Semgrep
- MITRE ATT&CK
- ATT&CK Navigator
- Tailscale
- Linux command-line tools
- Windows security tools
- Virtual machines and lab environments

---

# Documentation

Most projects in this repository include their own `README.md` and a dedicated report containing:

- Objective
- Methodology
- Technical steps
- Screenshots
- Findings
- Analysis
- Results
- Recommendations

This structure makes each training task independently reviewable while keeping the repository organized by cybersecurity domain.

---

# Training Program

**Program:** Masar Cybersecurity Training  
**Organization:** National Cyber Security Center

The repository represents selected practical exercises and project work completed during the program.

---


