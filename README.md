# Outbound Email Spam Detection Using Unsupervised Learning

## Project Overview
This project focuses on detecting **suspicious outbound emails** using **unsupervised machine learning** techniques. Leverage **Isolation Forest** for anomaly detection and **DBSCAN** for clustering, combined with **PCA** for dimensionality reduction and visualization. The project aims to identify anomalous behavior in email activity and provide actionable insights for email security monitoring.

---

## Objective
- Detect anomalous outbound.
- Understand patterns in email sending behavior that could indicate spam or compromised accounts.
- Provide interpretable insights by mapping principal components back to original email features.

---

## Dataset
- The dataset contains numeric features derived from email activity, including:
  - Number of recipients over different time periods (e.g., `Last6HrExtRcptCount`, `TodayExtRcptCount`)
  - Number of messages sent (e.g., `Last6HrMsgCount`)
  - Spam recipient counts (e.g., `Last1HrSpamRcptCount_Inbound`)
  - Account metadata (e.g., `AccountAgeInDays`, `PaidSeatCount`)
  - Other behavioral features (e.g., `MinutesFromSenderDomainFirstSeenToNow`, `ClientType`)

---

## Methodology
1. **Data Preprocessing**
   - Feature scaling.
   - PCA for dimensionality reduction.

2. **Unsupervised Learning**
   - **Isolation Forest**: Identifies anomalous emails based on isolation in the PCA feature space.
   - **DBSCAN**: Detects clusters of normal behavior and isolates noise points as potential anomalies.

3. **Evaluation & Analysis**
   - Visualize PCA components in 2D to explore clustering and anomalies.
   - Identify top PCA components contributing to anomalies.
   - Feature distributions of anomalies vs normal emails for key contributing features.

---

## Key Findings
- **Top PCA Components Contributing to Anomalies**: PC1, PC4, PC6, PC15, PC13.
- **Interpretation of Key Features**:
  - PC1: High recent outbound activity (`Last6HrExtRcptCount`, `Last6HrMsgCount`)
  - PC4: Inbound spam exposure (`TodaySpamRcptCount_Inbound`, `Last1HrSpamRcptCount_Inbound`)
  - PC6: Long-term internal spam behavior (`Last192HrIntraSpamMsgCount`)
  - PC15: Account age and sender/domain history (`MinutesFromSenderDomainFirstSeenToNow`)
  - PC13: Historical spam and client metadata (`Last30DaySpamRcptCount_Inbound`, `ClientType`)

- Anomalous emails typically exhibit **high recent activity**, **unusual sender/domain patterns**, or **internal/external spam interactions**.

---
