# Lazarus Group — TTP and MITRE ATT&CK Profile

## 1. APT Chosen

**Lazarus Group (G0032)** is a North Korean state-sponsored threat group associated with the Democratic People's Republic of Korea (DPRK) and attributed to the Reconnaissance General Bureau (RGB). The group has been active since at least 2009 and is also tracked under names including **HIDDEN COBRA, Labyrinth Chollima, ZINC, Diamond Sleet, and Guardians of Peace**. Lazarus operations have supported cyberespionage, financial theft, and disruptive objectives. **(Cite: [S1])**

This report examines the evolution of Lazarus Group by comparing **Operation Dream Job (2020)** with the **3CX supply-chain compromise (2023)**.

---

## 2. Campaign Evolution Comparison

### Campaign A — Operation Dream Job

**Period:** January–August 2020 UTC\
**Primary targets:** Defense, aerospace, government organizations, and selected employees.

Operation Dream Job used highly targeted social engineering built around fraudulent employment opportunities. Lazarus approached selected employees with convincing job offers and delivered malicious documents or links. Malicious Microsoft Office templates and Visual Basic macros were used to execute malware, while PowerShell and Windows Command Shell supported post-compromise activity. **(Cite: [S1], [S2])**

The campaign used custom malware including **Torisma**, with compromised web servers used as C2 infrastructure. Lazarus also established persistence through mechanisms such as malicious LNK files placed in the Windows Startup folder. **(Cite: [S1], [S3])**

### Campaign B — 3CX Supply-Chain Compromise

**Period:** March–April 2023 UTC\
**Primary targets:** 3CX and downstream organizations using the compromised 3CX Desktop App.

In 2023, North Korean-linked operators conducted a significantly different operation by compromising software supply chains. Mandiant determined that the initial compromise of 3CX originated from a previously trojanized **X_TRADER** software package distributed through the compromised Trading Technologies environment. The attackers subsequently compromised the 3CX Windows and macOS build environments and distributed malicious versions of the legitimate 3CX Desktop App. **(Cite: [S4])**

The compromised application executed a downloader known as **SUDDENICON**, retrieved encrypted C2 information from icon files hosted on GitHub, and ultimately downloaded **ICONICSTEALER**, which collected browser information. Within the 3CX environment, the attackers also used **TAXHAUL, COLDCAT, and POOLRAT**. **(Cite: [S4])**

Mandiant tracks this activity as **UNC4736** and assesses with moderate confidence that it is related to financially motivated North Korean AppleJeus activity. ESET research additionally identified technical links between Lazarus activity and the 3CX compromise. **(Cite: [S4], [S5])**

### TTP Evolution

| TTP Area              | Variant A — Operation Dream Job (2020)                                                                               | Variant B — 3CX (2023)                                                                                                                               |
| --------------------- | -------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Initial Access**    | Targeted job-themed spearphishing using malicious attachments, links, and social engineering. **(Cite: [S1], [S2])** | Compromised software supply chain using trojanized legitimate applications. **(Cite: [S4])**                                                         |
| **Execution**         | VBA macros, PowerShell, Windows Command Shell, and malicious DLL execution. **(Cite: [S1])**                         | Execution occurred through trojanized trusted software followed by multi-stage malicious components such as SUDDENICON. **(Cite: [S4])**             |
| **Persistence**       | Malicious LNK files were placed in Windows Startup locations. **(Cite: [S1])**                                       | TAXHAUL/COLDCAT persisted through DLL search-order hijacking involving the IKEEXT service; POOLRAT used Launch Daemons on macOS. **(Cite: [S4])**    |
| **C2**                | Torisma communicated with compromised web servers acting as C2 infrastructure. **(Cite: [S3])**                      | Encrypted icon files hosted on GitHub provided additional C2 information; additional infrastructure supported later malware stages. **(Cite: [S4])** |
| **Operational Reach** | Relied heavily on individually targeted social engineering against selected employees. **(Cite: [S2])**              | Compromising trusted software allowed malicious code to reach downstream organizations through legitimate software distribution. **(Cite: [S4])**    |

The comparison demonstrates an evolution from **target-focused social engineering and malicious documents** toward a more scalable **software supply-chain strategy**. The 2023 operation allowed the threat actor to exploit trust relationships between software vendors and their customers rather than requiring every victim to be individually deceived. **(Cite: [S2], [S4])**

---

## 3. Behavior Chain

### Initial Access

Lazarus commonly obtains initial access through targeted phishing and social engineering. During Operation Dream Job, the group impersonated recruiters and used malicious job-related attachments and links against selected employees. **(Cite: [S1], [S2])**

The 3CX campaign demonstrated an important evolution in this behavior: malicious software delivered through one compromised software supply chain ultimately enabled the compromise of another software vendor and its downstream customers. **(Cite: [S4])**

### Execution

Lazarus has used **PowerShell (T1059.001)**, **Windows Command Shell (T1059.003)**, and **Visual Basic (T1059.005)** for execution. Operation Dream Job specifically used malicious VBA macros and PowerShell/command-shell activity after compromise. **(Cite: [S1])**

In the 3CX operation, execution was instead embedded into trusted trojanized software and followed by multiple malware stages, including SUDDENICON and ICONICSTEALER. **(Cite: [S4])**

### Persistence

Lazarus has established persistence through **Registry Run Keys and Startup Folder mechanisms (T1547.001)**. During Operation Dream Job, malicious LNK files were placed in victims' Startup folders. **(Cite: [S1])**

During the 3CX compromise, TAXHAUL and COLDCAT achieved persistence through DLL search-order hijacking involving the IKEEXT service, while POOLRAT used Launch Daemons in the compromised macOS build environment. **(Cite: [S4])**

### Privilege Escalation

The 3CX intrusion demonstrated the ability to operate with elevated privileges after compromising critical infrastructure. On the Windows build environment, TAXHAUL and COLDCAT were configured through the IKEEXT service and executed with **LocalSystem privileges**, providing highly privileged execution. **(Cite: [S4])**

### Defense Evasion

Lazarus uses obfuscation, encrypted or encoded payloads, masquerading, signed code, file deletion, and trusted system binaries to reduce visibility of its activity. Operation Dream Job included software packing, encrypted/encoded files, masqueraded file types, code signing, and deletion of artifacts. **(Cite: [S1])**

The 3CX operation further demonstrated abuse of trusted software and signed applications, allowing malicious components to execute as part of software that users and organizations expected to be legitimate. **(Cite: [S4])**

### Discovery

After gaining access, Lazarus performs host and network discovery to understand the compromised environment. During Operation Dream Job, the group queried Active Directory servers for employee and administrator accounts and used PowerShell to explore compromised environments. **(Cite: [S1])**

### Lateral Movement

Lazarus has used compromised credentials and remote access to expand its position inside victim networks. MITRE documents Lazarus malware attempting connections to Windows shares using generated administrator usernames and weak passwords. **(Cite: [S1])**

During the 3CX intrusion, Mandiant reconstructed activity showing that the attackers harvested credentials and moved laterally before compromising both Windows and macOS build environments. **(Cite: [S4])**

### Command and Control

Lazarus frequently communicates over web protocols and compromised infrastructure. Torisma samples associated with Operation Dream Job communicated with multiple compromised web servers acting as C2 endpoints. **(Cite: [S1], [S3])**

During the 3CX campaign, SUDDENICON obtained additional C2 server information from encrypted icon files hosted on GitHub before subsequent malware stages communicated with attacker-controlled infrastructure. **(Cite: [S4])**

### Collection

Lazarus collects information from compromised hosts according to campaign objectives. Operation Dream Job included collection of local victim data and archival of collected information into RAR files. **(Cite: [S1])**

In the 3CX campaign, ICONICSTEALER collected application configuration information and browser history, providing information useful for subsequent access and intelligence gathering. **(Cite: [S4])**

### Exfiltration / Impact

Lazarus has exfiltrated collected information through C2 channels and web services. Operation Dream Job included both **Exfiltration Over C2 Channel** and exfiltration to cloud storage. **(Cite: [S1])**

The broader operational impact of the 3CX compromise was particularly significant because compromising a trusted software vendor enabled malicious software to propagate to downstream users through legitimate software distribution. **(Cite: [S4])**

---

## 4. MITRE ATT&CK Mapping

Impact scoring used for the ATT&CK Navigator layer:

- **High = 90**
- **Medium = 60**
- **Low = 30**

| Tactic              | ATT&CK ID     | Technique / Sub-technique                                             | Impact | Evidence                                                                                                                                                                                                                         |
| ------------------- | ------------- | --------------------------------------------------------------------- | -----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Initial Access      | **T1566.001** | Phishing: Spearphishing Attachment                                    |     90 | **Variant A (2020):** Dream Job used malicious job-themed attachments. **Variant B (2023):** 3CX shifted initial delivery toward compromised trusted software. **(Cite: [S1], [S4])**                                            |
| Execution           | **T1059.001** | Command and Scripting Interpreter: PowerShell                         |     60 | **Variant A (2020):** PowerShell was used to explore compromised environments and execute activity. **Variant B (2023):** execution increasingly relied on trojanized applications and staged malware. **(Cite: [S1], [S4])**    |
| Execution           | **T1059.003** | Command and Scripting Interpreter: Windows Command Shell              |     60 | Operation Dream Job used Windows Command Shell to launch DLLs and manipulate files and directories. **(Cite: [S1])**                                                                                                             |
| Execution           | **T1059.005** | Command and Scripting Interpreter: Visual Basic                       |     60 | Dream Job used malicious VBA macro code embedded in malicious Office content. **(Cite: [S1])**                                                                                                                                   |
| Persistence         | **T1547.001** | Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder |     90 | **Variant A (2020):** malicious LNK files were placed in Startup folders. **Variant B (2023):** persistence expanded to mechanisms associated with compromised build environments. **(Cite: [S1], [S4])**                        |
| Defense Evasion     | **T1027**     | Obfuscated Files or Information                                       |     60 | Lazarus has used packed and encrypted/encoded payloads; 3CX also used encrypted icon content to deliver C2 information. **(Cite: [S1], [S4])**                                                                                   |
| Defense Evasion     | **T1070.004** | Indicator Removal: File Deletion                                      |     60 | Lazarus has deleted malicious files and operational artifacts after execution, including during Operation Dream Job. **(Cite: [S1])**                                                                                            |
| Discovery           | **T1087.002** | Account Discovery: Domain Account                                     |     30 | During Operation Dream Job, Lazarus queried Active Directory servers to identify employees and administrator accounts. **(Cite: [S1])**                                                                                          |
| Discovery           | **T1083**     | File and Directory Discovery                                          |     30 | Lazarus malware and Dream Job activity searched victim file systems and directories during host reconnaissance. **(Cite: [S1])**                                                                                                 |
| Lateral Movement    | **T1110.003** | Brute Force: Password Spraying                                        |     60 | Lazarus malware has attempted connections to Windows shares using administrator username variations and weak passwords. **(Cite: [S1])**                                                                                         |
| Command and Control | **T1071.001** | Application Layer Protocol: Web Protocols                             |     60 | **Variant A (2020):** Torisma communicated with compromised web servers. **Variant B (2023):** staged malware used web-based infrastructure and encrypted GitHub-hosted content for C2 information. **(Cite: [S1], [S3], [S4])** |
| Collection          | **T1005**     | Data from Local System                                                |     60 | Lazarus has collected data directly from compromised systems during operations including Operation Dream Job. **(Cite: [S1])**                                                                                                   |
| Collection          | **T1560.001** | Archive Collected Data: Archive via Utility                           |     60 | Operation Dream Job archived victim data into RAR files before further handling or exfiltration. **(Cite: [S1])**                                                                                                                |
| Exfiltration        | **T1041**     | Exfiltration Over C2 Channel                                          |     90 | Lazarus malware has exfiltrated collected information through established C2 channels. **(Cite: [S1])**                                                                                                                          |

---

## 5. IoC Appendix

| # | Indicator                                                          | Type               | Decay Class   | Context                                                                                                  |
| - | ------------------------------------------------------------------ | ------------------ | ------------- | -------------------------------------------------------------------------------------------------------- |
| 1 | `9ae9ed06a69baa24e3a539d9ce32c437a6bdc136ce4367b1cb603e728f4279d5` | SHA-256 — Torisma  | **Durable**   | Operation Dream Job. **(Cite: [S3])**                                                                    |
| 2 | `f77a9875dbf1a1807082117d69bdbdd14eaa112996962f613de4204db34faba7` | SHA-256 — Torisma  | **Durable**   | Operation Dream Job. **(Cite: [S3])**                                                                    |
| 3 | `7762ba7ae989d47446da21cd04fd6fb92484dd07d078c7385ded459dedc726f9` | SHA-256 — Torisma  | **Durable**   | Operation Dream Job. **(Cite: [S3])**                                                                    |
| 4 | `0CA1723AFE261CD85B05C9EF424FC50290DCE7DF`                         | SHA-1 — SimplexTea | **Durable**   | Lazarus DreamJob activity technically linked by ESET to the 3CX investigation. **(Cite: [S5])**          |
| 5 | `3A63477A078CE10E53DFB5639E35D74F93CEFA81`                         | SHA-1 — OdicLoader | **Durable**   | Linux DreamJob activity associated with the Lazarus/3CX linkage. **(Cite: [S5])**                        |
| 6 | `journalide[.]org`                                                 | C2 Domain          | **Ephemeral** | C2 infrastructure associated with POOLRAT/SimplexTea and the 3CX-linked activity. **(Cite: [S4], [S5])** |

---

## Sources

**[S1] MITRE ATT&CK — Lazarus Group (G0032).**\
MITRE ATT&CK group profile documenting Lazarus Group, Operation Dream Job, associated software, and ATT&CK techniques.\
[https://attack.mitre.org/groups/G0032/](https://attack.mitre.org/groups/G0032/)

**[S2] ClearSky Cyber Security — Operation “Dream Job”: Widespread North Korean Espionage Campaign. 13 August 2020.**\
Research describing Lazarus social engineering through fake employment opportunities and targeting of defense, government, and related organizations.\
[https://www.clearskysec.com/operation-dream-job/](https://www.clearskysec.com/operation-dream-job/)

**[S3] JPCERT/CC — Operation Dream Job by Lazarus.**\
Technical analysis of Torisma and related Lazarus malware, including C2 infrastructure and malware hashes.\
[https://blogs.jpcert.or.jp/en/2021/01/Lazarus_malware2.html](https://blogs.jpcert.or.jp/en/2021/01/Lazarus_malware2.html)

**[S4] Mandiant — 3CX Software Supply Chain Compromise Initiated by a Prior Software Supply Chain Compromise; Suspected North Korean Actor Responsible. 20 April 2023.**\
Investigation describing the X_TRADER-to-3CX cascading supply-chain compromise, credential harvesting, lateral movement, persistence, malware, C2 infrastructure, and North Korean attribution.\
[https://cloud.google.com/blog/topics/threat-intelligence/3cx-software-supply-chain-compromise/](https://cloud.google.com/blog/topics/threat-intelligence/3cx-software-supply-chain-compromise/)

**[S5] ESET Research — Linux malware strengthens links between Lazarus and the 3CX supply-chain attack. 20 April 2023.**\
Research connecting Lazarus Operation DreamJob activity with the 3CX investigation and documenting Linux malware, infrastructure, and indicators.\
[https://www.welivesecurity.com/2023/04/20/linux-malware-strengthens-links-lazarus-3cx-supply-chain-attack/](https://www.welivesecurity.com/2023/04/20/linux-malware-strengthens-links-lazarus-3cx-supply-chain-attack/)

```
{
  "name": "Lazarus Group - Impact Based ATT&CK Mapping",
  "versions": {
    "attack": "18",
    "navigator": "5.2.0",
    "layer": "4.5"
  },
  "domain": "enterprise-attack",
  "description": "Impact-based MITRE ATT&CK mapping for Lazarus Group comparing Operation Dream Job (2020) and the 3CX Supply-Chain Compromise (2023). Scores: High=90, Medium=60, Low=30.",
  "filters": {
    "platforms": [
      "Windows",
      "Linux",
      "macOS"
    ]
  },
  "sorting": 0,
  "layout": {
    "layout": "side",
    "aggregateFunction": "average",
    "showID": true,
    "showName": true,
    "showAggregateScores": false,
    "countUnscored": false
  },
  "hideDisabled": false,
  "techniques": [
    {
      "techniqueID": "T1566.001",
      "score": 90,
      "comment": "Variant A (2020): Operation Dream Job used malicious job-themed spearphishing attachments. Variant B (2023): 3CX shifted initial delivery toward compromised trusted software. (Cite: [S1], [S4])",
      "enabled": true
    },
    {
      "techniqueID": "T1059.001",
      "score": 60,
      "comment": "Variant A (2020): PowerShell was used to explore compromised environments and execute activity. Variant B (2023): execution increasingly relied on trojanized applications and staged malware. (Cite: [S1], [S4])",
      "enabled": true
    },
    {
      "techniqueID": "T1059.003",
      "score": 60,
      "comment": "Operation Dream Job used Windows Command Shell to launch DLLs and manipulate files and directories. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1059.005",
      "score": 60,
      "comment": "Operation Dream Job used malicious VBA macro code embedded in malicious Office content. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1547.001",
      "score": 90,
      "comment": "Variant A (2020): malicious LNK files were placed in Startup folders. Variant B (2023): persistence expanded to mechanisms associated with compromised build environments. (Cite: [S1], [S4])",
      "enabled": true
    },
    {
      "techniqueID": "T1027",
      "score": 60,
      "comment": "Lazarus used packed and encrypted or encoded payloads. The 3CX operation also used encrypted icon content to provide C2 information. (Cite: [S1], [S4])",
      "enabled": true
    },
    {
      "techniqueID": "T1070.004",
      "score": 60,
      "comment": "Lazarus deleted malicious files and operational artifacts after execution, including during Operation Dream Job. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1087.002",
      "score": 30,
      "comment": "During Operation Dream Job, Lazarus queried Active Directory servers to identify employee and administrator accounts. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1083",
      "score": 30,
      "comment": "Lazarus malware and Operation Dream Job activity searched victim file systems and directories during host reconnaissance. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1110.003",
      "score": 60,
      "comment": "Lazarus malware attempted connections to Windows shares using administrator username variations and weak passwords. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1071.001",
      "score": 60,
      "comment": "Variant A (2020): Torisma communicated with compromised web servers. Variant B (2023): staged malware used web infrastructure and encrypted GitHub-hosted content for C2 information. (Cite: [S1], [S3], [S4])",
      "enabled": true
    },
    {
      "techniqueID": "T1005",
      "score": 60,
      "comment": "Lazarus collected data directly from compromised systems during operations including Operation Dream Job. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1560.001",
      "score": 60,
      "comment": "Operation Dream Job archived victim data into RAR files before further handling or exfiltration. (Cite: [S1])",
      "enabled": true
    },
    {
      "techniqueID": "T1041",
      "score": 90,
      "comment": "Lazarus malware exfiltrated collected information through established command-and-control channels. (Cite: [S1])",
      "enabled": true
    }
  ],
  "gradient": {
    "colors": [
      "#8ec843",
      "#ffff00",
      "#ff0000"
    ],
    "minValue": 30,
    "maxValue": 90
  },
  "legendItems": [
    {
      "label": "Low Impact - 30",
      "color": "#8ec843"
    },
    {
      "label": "Medium Impact - 60",
      "color": "#ffff00"
    },
    {
      "label": "High Impact - 90",
      "color": "#ff0000"
    }
  ],
  "metadata": [
    {
      "name": "Scoring",
      "value": "High = 90, Medium = 60, Low = 30"
    },
    {
      "name": "Campaign A",
      "value": "Operation Dream Job (2020)"
    },
    {
      "name": "Campaign B",
      "value": "3CX Supply-Chain Compromise (2023)"
    }
  ],
  "links": [],
  "showTacticRowBackground": false,
  "tacticRowBackground": "#dddddd",
  "selectTechniquesAcrossTactics": true,
  "selectSubtechniquesWithParent": false
}
```
