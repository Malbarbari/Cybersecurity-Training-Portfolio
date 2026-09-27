# BazaarJo Business Impact Analysis (BIA)

## 1. Introduction

Following the security breach and service disruption, BazaarJo's website was unavailable for approximately two hours. This caused loss of sales, merchant complaints, customer refunds, and negative social media coverage.

The purpose of this Business Impact Analysis (BIA) is to identify BazaarJo's most critical business processes, determine their impact if disrupted, identify their dependencies, and define suitable Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO).

---

## 2. Critical Business Processes

The following six processes were identified as critical to BazaarJo's business operations:

1. Online Shopping / Order Processing
2. Payment Processing
3. Customer Account Management
4. Merchant Operations
5. Customer Support
6. Website and Application Operations

---

## 3. Completed BIA Table

| Rank | Business Process | Key System Dependencies | People Dependencies | Vendor Dependencies | Financial Impact | Customer Impact | Regulatory / Legal Impact | RTO | RPO |
|---:|---|---|---|---|---|---|---|---|---|
| 1 | Online Shopping / Order Processing | Web App, Database, API, Inventory System | DevOps, Operations | Hosting / Cloud Provider | H | H | M | 1 Hour | 15 Min |
| 2 | Payment Processing | Payment API, Database, Web App | Finance, DevOps | Payment Gateway, Bank | H | H | H | 1 Hour | 5 Min |
| 3 | Website & Application Operations | Web Server, Application Server, DNS, CI/CD | DevOps, IT Operations | Cloud/Hosting, DNS Provider | H | H | M | 1 Hour | 15 Min |
| 4 | Merchant Operations | Merchant Portal, Database, APIs | Merchant Support, Operations | Payment/Logistics Providers | M | H | M | 4 Hours | 1 Hour |
| 5 | Customer Support | Support Platform, Customer Database, Email/Chat | Customer Support Team | Email/Communication Provider | M | H | M | 4 Hours | 1 Hour |
| 6 | Customer Account Management | Authentication System, Database, Web App | IT Support, Security Team | Email/SMS/OTP Provider | M | H | H | 4 Hours | 30 Min |

---

## 4. BIA Impact Assessment

### 4.1 Online Shopping / Order Processing

This is one of BazaarJo's most critical processes because it directly generates sales. If customers cannot browse products or place orders, BazaarJo immediately loses revenue.

- Financial Impact: **High**
- Customer Impact: **High**
- Regulatory/Legal Impact: **Medium**
- RTO: **1 Hour**
- RPO: **15 Minutes**

The short RTO is required because every hour of downtime can result in lost orders and additional customer complaints.

### 4.2 Payment Processing

Payment processing is critical because it allows completed orders to generate revenue. A failure can also result in failed transactions, duplicate payments, refunds, and customer disputes.

- Financial Impact: **High**
- Customer Impact: **High**
- Regulatory/Legal Impact: **High**
- RTO: **1 Hour**
- RPO: **5 Minutes**

The RPO is very short because payment transaction data must not be lost or become inconsistent.

### 4.3 Website & Application Operations

The website and application infrastructure provides access to most of BazaarJo's services. A failure can make shopping, account access, merchant operations, and other services unavailable.

- Financial Impact: **High**
- Customer Impact: **High**
- Regulatory/Legal Impact: **Medium**
- RTO: **1 Hour**
- RPO: **15 Minutes**

The website should be restored quickly because the previous two-hour outage already caused measurable business damage.

### 4.4 Merchant Operations

Merchant operations allow sellers to manage products, orders, and their business activities on BazaarJo.

- Financial Impact: **Medium**
- Customer Impact: **High**
- Regulatory/Legal Impact: **Medium**
- RTO: **4 Hours**
- RPO: **1 Hour**

Merchant services are important but can tolerate a longer disruption than the core shopping and payment functions.

### 4.5 Customer Support

Customer support handles complaints, refund requests, order problems, and communication with customers.

- Financial Impact: **Medium**
- Customer Impact: **High**
- Regulatory/Legal Impact: **Medium**
- RTO: **4 Hours**
- RPO: **1 Hour**

Customer support is important during incidents because it reduces customer dissatisfaction and helps manage refunds and complaints.

### 4.6 Customer Account Management

Account management includes login, authentication, customer profiles, and account-related information.

- Financial Impact: **Medium**
- Customer Impact: **High**
- Regulatory/Legal Impact: **High**
- RTO: **4 Hours**
- RPO: **30 Minutes**

The regulatory/legal impact is considered high because customer account information may contain personal data that must be protected and maintained accurately.

---

## 5. RTO and RPO Justification

### RTO – Recovery Time Objective

RTO defines the maximum acceptable time that a business process can remain unavailable before the impact becomes unacceptable.

BazaarJo's most critical customer-facing services were assigned an RTO of **1 hour**. This is because the previous two-hour website outage resulted in:

- Loss of sales
- Customer complaints
- Refunds
- Negative social media coverage

Less critical supporting processes were assigned an RTO of **4 hours**, since they can tolerate a longer interruption without completely stopping the core business.

### RPO – Recovery Point Objective

RPO defines the maximum acceptable amount of data loss measured in time.

Payment processing has the lowest RPO of **5 minutes** because losing transaction data could cause financial discrepancies, duplicate transactions, or incorrect payment status.

Order processing and website systems have an RPO of **15 minutes** to reduce the amount of lost order and application data.

Supporting services were assigned an RPO of **30–60 minutes** based on their lower recovery priority.

---

## 6. Process Ranking

### Priority 1 – Online Shopping / Order Processing

This process is the main source of revenue for BazaarJo. If customers cannot place orders, BazaarJo immediately loses sales.

**RTO: 1 Hour | RPO: 15 Minutes**

### Priority 2 – Payment Processing

Payment processing is required to complete sales and involves financial transactions and potential regulatory requirements.

**RTO: 1 Hour | RPO: 5 Minutes**

### Priority 3 – Website & Application Operations

The website and application infrastructure provides access to the majority of BazaarJo's services. Its failure can affect customers, merchants, and order processing simultaneously.

**RTO: 1 Hour | RPO: 15 Minutes**

### Priority 4 – Merchant Operations

Important for maintaining relationships with BazaarJo's sellers and managing products and orders.

**RTO: 4 Hours | RPO: 1 Hour**

### Priority 5 – Customer Support

Important for handling complaints, refunds, and communication during service disruptions.

**RTO: 4 Hours | RPO: 1 Hour**

### Priority 6 – Customer Account Management

Important for customer access and personal data, but a temporary disruption does not immediately stop all sales.

**RTO: 4 Hours | RPO: 30 Minutes**

---

## 7. Top 3 Critical Processes

### 1. Online Shopping / Order Processing

- **Impact:** High Financial / High Customer
- **RTO:** 1 Hour
- **RPO:** 15 Minutes
- **Why:** Directly generates sales and is the main customer-facing business process.

### 2. Payment Processing

- **Impact:** High Financial / High Customer / High Legal
- **RTO:** 1 Hour
- **RPO:** 5 Minutes
- **Why:** Required to complete transactions and protect financial transaction data.

### 3. Website & Application Operations

- **Impact:** High Financial / High Customer
- **RTO:** 1 Hour
- **RPO:** 15 Minutes
- **Why:** Provides access to shopping, accounts, orders, and other BazaarJo services.

---

## 8. Conclusion

The BIA shows that BazaarJo's highest priorities are the processes directly responsible for sales, payments, and website availability.

The previous two-hour outage demonstrates that BazaarJo cannot tolerate long interruptions to these services. Therefore, the three highest-priority processes should have an RTO of approximately one hour, with frequent backups and recovery mechanisms to meet their RPO requirements.

BazaarJo should prioritize recovery of online ordering, payment processing, and website/application infrastructure during future incidents. Supporting processes such as merchant operations, customer support, and account management can follow according to their lower recovery priority.
