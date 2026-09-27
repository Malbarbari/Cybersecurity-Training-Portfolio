# Semgrep SAST Integration with GitHub Actions

This repository contains an assessment demonstrating the integration of
**Semgrep SAST (Static Application Security Testing)** into a **GitHub
Actions CI/CD workflow** for the **OWASP Juice Shop** project.

The exercise demonstrates how source code can be automatically scanned
for security findings whenever new code is pushed to a GitHub
repository.

## Overview

The assessment follows this workflow:

1.  Fork the OWASP Juice Shop repository.
2.  Clone the fork to Kali Linux.
3.  Create a Semgrep GitHub Actions workflow.
4.  Commit and push the workflow.
5.  Verify the first automatic Semgrep scan.
6.  Review the initial scan results.
7.  Add a new Python source file.
8.  Commit and push the new code.
9.  Verify that the push automatically triggers another Semgrep scan.
10. Review the final scan results.

## Tools Used

-   **Git / GitHub** --- source-code version control and repository
    hosting.
-   **GitHub Actions** --- CI/CD automation.
-   **Semgrep** --- Static Application Security Testing (SAST).
-   **Kali Linux** --- local environment used to clone and modify the
    repository.
-   **OWASP Juice Shop** --- intentionally vulnerable web application
    used as the project codebase.

## GitHub Actions Workflow

The workflow is located at:

``` text
.github/workflows/semgrep-sast.yml
```

Its main configuration is:

``` yaml
name: Semgrep SAST

on:
  push:

jobs:
  semgrep:
    name: Semgrep SAST Scan
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Source Code
        uses: actions/checkout@v4

      - name: Install Semgrep
        run: pip install semgrep

      - name: Run Semgrep SAST Scan
        run: semgrep scan --config auto .
```

The `push` trigger means that the workflow automatically starts whenever
changes are pushed to the repository.

## Scan Results

### Initial Scan

The first scan reported:

-   **Targets scanned:** 1,028
-   **Rules run:** 408
-   **Findings:** 70
-   **Blocking findings:** 70
-   **Parsed lines:** \~99.9%

### Final Scan

After adding `semgrep_demo.py`, the second scan reported:

-   **Targets scanned:** 1,029
-   **Rules run:** 650
-   **Findings:** 70
-   **Blocking findings:** 70
-   **Parsed lines:** \~99.9%

The increase from **1,028 to 1,029 targets** confirms that the newly
added Python file was included in the subsequent scan.

## Repository Structure

``` text
Semgrep-SAST-GitHub-Actions/
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

## Report

The complete step-by-step assessment with commands, configuration, scan
results, and screenshots is available in:

**[Penetration Testing / SAST Assessment Report](report.md)**

## Conclusion

This exercise demonstrates a CI/CD security workflow in which Semgrep
automatically performs SAST analysis whenever code is pushed to the
repository.

The implementation successfully:

-   Integrated Semgrep with GitHub Actions.
-   Scanned the OWASP Juice Shop source code.
-   Reported security findings through the GitHub Actions runner.
-   Automatically triggered a second scan after a source-code change.
-   Confirmed that the newly added source file was included in the
    subsequent scan.

## Disclaimer

This project was performed for educational and authorized
security-testing purposes. The techniques and configurations documented
here should only be applied to repositories and systems for which you
have permission to perform security testing.
