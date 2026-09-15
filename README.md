# SOC114-Malicious-Attachment-Phishing-Investigation
SOC L1 investigation of a malicious attachment phishing alert using email analysis, log investigation, IOC identification, and endpoint containment.


# SOC114 - Malicious Attachment Phishing Investigation

## 📌 Overview

This project documents a SOC L1 investigation of a phishing alert involving a malicious email attachment.

The investigation was performed in a simulated LetsDefend environment using email analysis, log investigation, IOC identification, and endpoint containment.

---

## 🚨 Alert Information

| Field | Details |
|---|---|
| Alert | SOC114 - Malicious Attachment Detected - Phishing Alert |
| Severity | High |
| Alert Type | Exchange |
| Event ID | 45 |
| Role | Security Analyst |
| Email Subject | Invoice |
| Sender | accounting@cmail.carleton.ca |
| Recipient | richard@letsdefend.io |
| SMTP Address | 49.234.43.39 |
| Device Action | Allowed |
| MITRE ATT&CK | T1598.001 |

---

## 🔍 Investigation Process

### 1. Parse Email

The email details were reviewed to identify:

- Sender address
- Recipient address
- SMTP address
- Email subject
- Delivery status
- Attachments/URLs
- Suspicious email content

The email contained a suspicious attachment.

---

### 2. Check Email Delivery

The alert showed:

**Device Action: Allowed**

This indicated that the email was allowed to reach the user.

**Result: Delivered**

---

### 3. Identify Malicious Activity

The investigation required checking whether the malicious attachment or URL was accessed.

The suspicious C2 domain identified for the investigation was:

`andaluciabeach.net`

This domain was searched in Log Management.

---

### 4. Log Investigation

The search returned **1 event**.

Important evidence:

```text
Process: EQNEDT32.EXE
Parent Process: excel.exe
Request URL: http://andaluciabeach.net/image/network.exe
Device Action: Allowed
