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
Process Chain
excel.exe
    ↓
EQNEDT32.EXE
    ↓
http://andaluciabeach.net/image/network.exe

This was treated as evidence of malicious activity on the endpoint.

🌐 Indicators of Compromise (IOCs)
Type	Indicator	Description
Domain	andaluciabeach.net	Suspicious C2 domain
URL	http://andaluciabeach.net/image/network.exe	Suspicious executable request
Process	EQNEDT32.EXE	Suspicious process
Parent Process	excel.exe	Parent process
🛡️ Containment

Because malicious activity was observed on the endpoint, the affected user machine was identified for containment using EDR.

The purpose of containment was to isolate the affected endpoint and prevent further communication or potential lateral movement.

✅ Investigation Verdict

Verdict: Malicious / Phishing

Evidence Summary
Malicious attachment was detected.
Email was delivered to the recipient.
Suspicious C2 infrastructure was identified.
Log Management showed communication with the suspicious domain.
EQNEDT32.EXE was observed with excel.exe as its parent process.
A suspicious executable URL was requested.
Endpoint containment was required.
🧠 Skills Practiced
Phishing Email Analysis
Email Header/Metadata Analysis
IOC Identification
Domain Investigation
Log Management
Process Analysis
C2 Investigation
EDR Containment
SOC Alert Investigation
Incident Response
🛠️ Tools / Platforms
LetsDefend
Log Management
EDR
Email Security
Threat Intelligence
📚 Key Learning

This investigation demonstrated the basic SOC workflow:

Alert
  ↓
Email Analysis
  ↓
Identify IOC
  ↓
Search Logs
  ↓
Analyze Evidence
  ↓
Confirm Malicious Activity
  ↓
Contain Endpoint
  ↓
Document Investigation
