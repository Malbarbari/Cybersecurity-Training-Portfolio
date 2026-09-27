# Penetration Testing Assessment

This repository contains a penetration testing assessment performed
against a provided vulnerable Virtual Machine environment.

The assessment focuses on **network enumeration, web application
discovery, vulnerability identification, exploitation, and
proof-of-concept validation**.

## Assessment Overview

**Target:** `10.10.10.100`

### Methodology

The assessment followed these main phases:

1.  **Information Gathering & Enumeration**
    -   Nmap service and version detection.
    -   Identification of exposed TCP services.
2.  **Web Directory Enumeration**
    -   Metasploit `scanner/http/dir_scanner`.
    -   Discovery of `/blog/` and `/login/`.
3.  **Web Application Analysis**
    -   Inspection of the discovered blog.
    -   Identification of the technology used by the application.
4.  **Vulnerability Identification**
    -   Searching Metasploit for a relevant exploit based on the
        identified technology.
5.  **Exploitation**
    -   Configuration and execution of the identified exploit.
    -   Successful Remote Command Execution (RCE).
6.  **Proof of Concept**
    -   Access to an interactive system shell.
    -   Execution of `uname -a` to verify command execution and obtain
        system information.

## Repository Structure

``` text
Penetration_Testing_Assessment_Report/
├── README.md
├── report.md
└── screenshots/
    ├── image1.png
    ├── image2.png
    ├── image3.png
    ├── image4.png
    ├── image5.png
    ├── image6.png
    ├── image7.png
    ├── image8.png
    ├── image9.png
    ├── image10.png
    └── image11.png
```

## Tools Used

-   **Nmap** --- network and service enumeration.
-   **Metasploit Framework** --- web directory enumeration and
    exploitation.
-   **Linux shell** --- post-exploitation verification.
-   **`uname -a`** --- kernel and operating-system information
    gathering.

## Key Results

The assessment identified:

-   SSH exposed on **port 22**.
-   Apache HTTP service exposed on **port 80**.
-   Web directories including `/blog/` and `/login/`.
-   A vulnerable web application component that could be exploited.
-   Successful **Remote Command Execution (RCE)** on the target.
-   Successful execution of a system command from the compromised
    environment.

## Report

The complete assessment, including commands, findings, screenshots,
exploitation steps, and proof of concept, is available in:

**[Penetration Testing Assessment Report](report.md)**

## Disclaimer

This assessment was performed against an intentionally provided
lab/virtual-machine environment for educational and authorized
penetration-testing purposes. The techniques documented here should only
be used against systems for which you have explicit permission to test.
