# Lazarus Group TTP & MITRE ATT&CK Profile

A cybersecurity threat-intelligence project analyzing the **Lazarus Group (G0032)** and comparing the evolution of its tactics, techniques, and procedures across two major campaigns:

- **Operation Dream Job (2020)**
- **3CX Supply-Chain Compromise (2023)**

The project focuses on how Lazarus evolved from highly targeted social-engineering operations toward more scalable supply-chain compromise techniques.

---

## Project Overview

This repository documents the behavior of the Lazarus Group across multiple stages of the attack lifecycle.

The analysis includes:

- Threat actor background
- Campaign comparison
- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion
- Discovery
- Lateral Movement
- Command and Control
- Collection
- Exfiltration and Impact
- MITRE ATT&CK mapping
- Impact-based ATT&CK scoring
- Indicators of Compromise (IoCs)
- ATT&CK Navigator JSON configuration

---

## Campaigns Compared

### Operation Dream Job — 2020

Operation Dream Job relied heavily on targeted social engineering using fraudulent employment opportunities.

Observed techniques included:

- Spearphishing attachments
- Malicious Office documents
- VBA macros
- PowerShell
- Windows Command Shell
- Startup-folder persistence
- Custom malware such as Torisma

### 3CX Supply-Chain Compromise — 2023

The 3CX campaign demonstrated a major shift toward compromising trusted software supply chains.

Observed activity included:

- Trojanized legitimate software
- Multi-stage malware execution
- Encrypted C2 configuration
- Credential harvesting
- Lateral movement
- Build-environment compromise
- Windows and macOS targeting
- Downstream compromise through legitimate software distribution

---

## TTP Evolution

A key finding of the project is the shift from:

**Targeted social engineering against individual users**

to:

**Compromising trusted software vendors to reach many downstream organizations**

This demonstrates an evolution in operational scale, delivery methods, and abuse of trust relationships.

---

## MITRE ATT&CK Mapping

The project maps Lazarus behavior to ATT&CK techniques including:

| ATT&CK ID | Technique |
|---|---|
| T1566.001 | Spearphishing Attachment |
| T1059.001 | PowerShell |
| T1059.003 | Windows Command Shell |
| T1059.005 | Visual Basic |
| T1547.001 | Registry Run Keys / Startup Folder |
| T1027 | Obfuscated Files or Information |
| T1070.004 | File Deletion |
| T1087.002 | Domain Account Discovery |
| T1083 | File and Directory Discovery |
| T1110.003 | Password Spraying |
| T1071.001 | Web Protocols |
| T1005 | Data from Local System |
| T1560.001 | Archive via Utility |
| T1041 | Exfiltration Over C2 Channel |

The ATT&CK Navigator scoring model used in the report is:

- **High Impact = 90**
- **Medium Impact = 60**
- **Low Impact = 30**

---

## Indicators of Compromise

The report includes indicators associated with Lazarus activity and the analyzed campaigns, including:

- Torisma SHA-256 hashes
- SimplexTea SHA-1
- OdicLoader SHA-1
- C2 infrastructure associated with 3CX-linked activity

Indicators are categorized according to their expected durability.

---

## Repository Structure

```text
lazarus-group-ttp-analysis/
│
├── README.md
└── Lazarus_Group_TTP_MITRE_ATTCK_Profile.md
```

---

## Full Report

The complete technical report is available here:

**[Lazarus_Group_TTP_MITRE_ATTCK_Profile.md](./Lazarus_Group_TTP_MITRE_ATTCK_Profile.md)**

---

## Skills Demonstrated

- Threat Intelligence
- APT Research
- MITRE ATT&CK
- ATT&CK Navigator
- TTP Analysis
- Campaign Comparison
- Indicators of Compromise Analysis
- Threat Actor Profiling
- Cyber Threat Analysis

---

## Disclaimer

This project was created for **educational, academic, threat-intelligence, and defensive cybersecurity purposes only**.

The repository does not distribute malware or provide instructions intended to enable malicious activity.
