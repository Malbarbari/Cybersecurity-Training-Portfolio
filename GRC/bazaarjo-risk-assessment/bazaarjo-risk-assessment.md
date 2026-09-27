# BazaarJo Cybersecurity Risk Assessment and Treatment Report

## 1. Risk Context Summary

BazaarJo’s main business objectives at risk are protecting customer information, maintaining secure e-commerce services, ensuring payment security, and maintaining customer trust.

The incident creates regulatory exposure under the Jordanian Personal Data Protection Law (PDPL) and PCI DSS requirements for payment-card data.

BazaarJo has a **very low risk appetite for customer data exposure and regulatory violations** because they may result in legal, financial, and reputational consequences. The company also has a **low risk appetite for service downtime**, as disruption directly affects sales and customer experience. BazaarJo has a **low risk appetite for reputational damage**, because loss of customer trust can reduce future business and increase recovery costs.

---

## 2. Risk Identification – Risk Register

| # | Risk | Asset | Threat | Vulnerability |
|---|---|---|---|---|
| R1 | Customer personal data exposure | Customer database / PII | Cyber attacker | Weak access controls and compromised accounts |
| R2 | Payment-card data compromise | Payment environment / cardholder data | Cyber attacker | Insufficient protection and monitoring of sensitive payment systems |
| R3 | Unauthorized modification of source code | Source code / production applications | Attacker using stolen developer credentials | Weak developer authentication and insufficient code approval controls |
| R4 | Extended e-commerce service outage | Web platform / production services | Attacker or malicious code | Weak change control, recovery and incident response capabilities |
| R5 | Regulatory and legal penalties | Compliance records / customer data | Regulatory investigation | Lack of PDPL alignment and inadequate incident governance |
| R6 | Loss of customer trust and reputation | Brand / customer relationships | Public disclosure of breach | Poor incident communication and insufficient security governance |
| R7 | Third-party/vendor security compromise | Vendor systems / shared data | Compromised supplier | Weak vendor security assessment and oversight |
| R8 | Inability to detect and respond to future incidents | Logs / security monitoring capability | Continued attacker activity | Insufficient monitoring, unclear CISO accountability and weak SOC governance |

---

## 3. Risk Analysis – Likelihood & Impact

**Risk rating:**

- Low = Limited business effect
- Medium = Significant business effect
- High = Severe business effect requiring management attention

| Risk | Likelihood | Impact | Overall Risk | Business Impact |
|---|---|---|---|---|
| **R1 – Customer data exposure** | High | High | **Critical** | Financial, Regulatory, Reputational |
| **R2 – Payment-card data compromise** | Medium | High | **High** | Financial, Regulatory, Reputational |
| **R3 – Source code modification** | High | High | **Critical** | Operational, Financial, Reputational |
| **R4 – E-commerce service outage** | Medium | High | **High** | Operational, Financial, Reputational |
| **R5 – Regulatory/legal penalties** | High | High | **Critical** | Regulatory, Financial, Reputational |
| **R6 – Customer trust/reputation loss** | High | High | **Critical** | Reputational, Financial |
| **R7 – Vendor security compromise** | Medium | High | **High** | Regulatory, Operational, Reputational |
| **R8 – Poor detection and response** | High | Medium | **High** | Operational, Financial, Regulatory |

### Rating Justifications

**R1 – Customer Data Exposure:**  
Likelihood is High because the breach has already demonstrated weaknesses around protection of customer information. Impact is High because exposure of personal data can create regulatory obligations, customer complaints, compensation costs, and long-term loss of trust.

**R3 – Source Code Modification:**  
Likelihood is High because stolen developer credentials can allow unauthorized changes if strong authentication and approval controls are missing. Impact is High because malicious code changes could affect production systems, create additional vulnerabilities, cause outages, or lead to another compromise.

**R5 – Regulatory and Legal Penalties:**  
Likelihood is High because the incident involves personal and potentially payment-related information and BazaarJo has identified governance and compliance gaps. Impact is High because regulatory investigations, penalties, legal costs, and mandatory corrective actions can create significant financial and operational pressure.

---

## 4. Risk Evaluation & Top 3 Priorities

### 1. Customer Data Exposure – R1

**Priority: Critical**

This is the highest priority because it directly affects customers and creates both regulatory and reputational consequences. A data breach can result in legal obligations, customer complaints, financial losses, and long-term damage to BazaarJo’s brand.

### 2. Unauthorized Source Code Modification – R3

**Priority: Critical**

This risk can create cascading effects beyond the original breach. Unauthorized code changes could introduce backdoors, disrupt production services, compromise additional data, or create another security incident. Therefore, it can affect confidentiality, integrity, and availability simultaneously.

### 3. Regulatory & Legal Exposure – R5

**Priority: Critical**

Regulatory exposure can increase the overall cost of the incident and force BazaarJo to perform corrective actions under management and regulatory pressure. It also overlaps with the customer-data risk and can worsen reputational damage.

**Why these three outrank the others:**  
They have the strongest combination of **regulatory exposure, direct brand impact, financial consequences, and cascading operational effects**. Addressing them also reduces several of the other identified risks.

---

## 5. Risk Treatment Decisions

| Risk | Decision | High-Level Treatment Actions | Risk Owner |
|---|---|---|---|
| **R1 – Customer Data Exposure** | **Mitigate** | Strengthen access controls and MFA, review data access privileges, encrypt sensitive data, improve monitoring, conduct breach assessment and ensure PDPL compliance. | CISO / Data Protection Officer |
| **R3 – Source Code Modification** | **Mitigate** | Enforce MFA for developers, privileged-access controls, branch protection, mandatory code review, secure SDLC approvals, secrets management and monitoring of developer accounts. | CISO / Head of Engineering |

**Management decision:**  
Both risks should be **mitigated rather than accepted**, because their potential impact exceeds BazaarJo’s risk appetite.

---

## 6. Monitoring & Reporting

### Key Risk Indicators (KRIs)

1. **Number of failed or suspicious privileged-account login attempts**
2. **Number of users/developers without MFA**
3. **Number of unauthorized or emergency production code changes**
4. **Number of unresolved high-severity security incidents**
5. **Number of critical vendors without completed security assessments**

### Reporting Frequency

- **KRIs:** Continuous monitoring with **weekly management review**
- **Risk register:** **Monthly** review
- **Critical risks:** Immediate escalation when thresholds are exceeded
- **Board-level risk report:** **Monthly or quarterly**, depending on severity

### Reporting Flow

**SOC / Security Team → CISO → Risk Management / Compliance → Executive Management → Board**

The **CISO** should provide the technical security risk view, **Legal/Compliance** should assess regulatory exposure, and **Risk Management** should maintain the overall risk register and escalation process.
