# Lumma Stealer Malware Analysis & MITRE ATT&CK Mapping

A cybersecurity research project focused on analyzing **Lumma Stealer (LummaC2)**, a Windows-based information-stealing malware family, and mapping its observed behavior to the **MITRE ATT&CK Enterprise framework**.

The project examines Lumma's infection methods, execution techniques, persistence mechanisms, credential theft capabilities, command-and-control infrastructure, defense evasion techniques, indicators of compromise, and defensive recommendations.

---

## Project Overview

Lumma Stealer is an information-stealing malware distributed using a **Malware-as-a-Service (MaaS)** model.

The objective of this project was to study the malware from a defensive cybersecurity perspective and translate its observed behaviors into MITRE ATT&CK techniques that can be used for threat detection, threat hunting, and incident response.

The analysis covers:

- Malware delivery techniques
- Execution methods
- Persistence mechanisms
- System and browser discovery
- Credential and session cookie theft
- Cryptocurrency wallet targeting
- Data collection and staging
- Command-and-Control communication
- Data exfiltration
- Defense evasion techniques
- Indicators of Compromise (IoCs)
- MITRE ATT&CK mapping
- Detection recommendations
- System hardening recommendations
- Incident response considerations

---

## MITRE ATT&CK Mapping

The observed Lumma behaviors were mapped to the **MITRE ATT&CK Enterprise framework**.

Some of the important techniques covered in the analysis include:

| Technique | Description |
|---|---|
| T1566.001 | Spearphishing Attachment |
| T1566.002 | Spearphishing Link |
| T1059.001 | PowerShell |
| T1218.005 | System Binary Proxy Execution: Mshta |
| T1055.012 | Process Injection: Process Hollowing |
| T1547.001 | Registry Run Keys / Startup Folder |
| T1555.003 | Credentials from Web Browsers |
| T1539 | Steal Web Session Cookie |
| T1113 | Screen Capture |
| T1119 | Automated Collection |
| T1071.001 | Application Layer Protocol: Web Protocols |
| T1041 | Exfiltration Over C2 Channel |

A scoring system was also used to represent the relevance and potential security impact of each technique in the Lumma attack lifecycle.

---

## Key Findings

Lumma primarily focuses on stealing sensitive information from compromised Windows systems.

The malware can target:

- Browser passwords
- Browser authentication cookies
- Autofill information
- Cryptocurrency wallets
- VPN configuration files
- FTP client information
- Telegram data
- User documents
- System information

Lumma campaigns have also used techniques such as:

- Phishing
- Malvertising
- Trojanized software
- Fake CAPTCHA / ClickFix attacks
- PowerShell execution
- MSHTA abuse
- AutoIT
- DLL side-loading
- Process hollowing
- Reflective code loading

---

## Detection Strategy

The project emphasizes **behavior-based detection** rather than relying only on static hashes or domains.

Examples of useful monitoring areas include:

- Suspicious PowerShell execution
- Base64 or encoded PowerShell commands
- `mshta.exe` making external network connections
- Unexpected AutoIT execution
- Process injection or process hollowing
- Suspicious access to browser credential databases
- Registry modifications to Windows Run keys
- Executables running from `AppData` or `Temp`
- Unknown processes making repeated external HTTPS connections

---

## Defensive Recommendations

The report discusses several defensive controls including:

- Endpoint Detection and Response (EDR)
- PowerShell Script Block Logging
- PowerShell Module Logging
- PowerShell Transcription
- Application control using AppLocker or WDAC
- DNS and web filtering
- Email security controls
- Browser protection
- Least privilege
- Software installation restrictions
- Security awareness training

Special attention is given to **ClickFix / fake CAPTCHA attacks**, where victims are tricked into manually executing malicious commands.

---

## Incident Response

Because Lumma targets credentials and authenticated sessions, simply deleting the malware executable may not be enough.

A proper response may require:

1. Isolating the affected endpoint.
2. Removing malicious files and persistence mechanisms.
3. Preserving forensic evidence.
4. Resetting potentially exposed passwords.
5. Revoking active sessions.
6. Revoking authentication tokens.
7. Reviewing MFA registrations.
8. Reviewing VPN, email, cloud, and identity logs.
9. Hunting for Lumma-related IoCs and behaviors across the environment.
10. Investigating whether additional malware was installed.

---

## Repository Structure

```text
Lumma-Stealer-Analysis/
│
├── README.md
├── Lumma_Stealer_Analysis.md
│
└── screenshots/
    ├── image1.png
    ├── image2.png
    ├── image3.png
    └── ...
```

---

## Full Report

The complete technical analysis is available here:

**[Lumma Stealer Analysis Report](./Lumma_Stealer_Analysis.md)**

---

## Disclaimer

This project was created for **educational, malware research, threat intelligence, and defensive cybersecurity purposes only**.

The information provided is intended to help understand malware behavior, MITRE ATT&CK mapping, detection strategies, and defensive security practices.

No malware is distributed through this repository.

---

## Skills Demonstrated

- Malware Research
- Threat Intelligence
- MITRE ATT&CK
- Indicators of Compromise Analysis
- Threat Hunting
- Detection Engineering
- Endpoint Security
- Incident Response
- Cyber Threat Analysis

---

## Author

**Mohammad Ali**

Cybersecurity Student