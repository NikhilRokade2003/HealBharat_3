
# Hospital Web Application – Security Audit Overview

##  Overview

This repository documents the security architecture and vulnerabilities found in the **Hospital Web Portal** developed for **Heal Bharat**.

The system allows:
- **Doctor/Patient Login**
- Access to **Health Records**
- API integrations with **Lab Reports** and **Insurance**
- **Output generation** (View/Edit Records)

However, the architecture currently lacks critical security implementations, exposing sensitive medical data to numerous risks.

---

## Identified Security Flow

![Security_Flowchart](https://github.com/user-attachments/assets/c346088e-38d7-43d4-9de0-de6439c9aafc)

---

##  Top 5 Critical Threats

| # | Threat Description                              | Risk Category         |
|---|--------------------------------------------------|------------------------|
| 1 | No role-based access control                     | Access Control         |
| 2 | Unencrypted login (no HTTPS or 2FA)              | Authentication/Data-in-Transit |
| 3 | Plain-text patient records in DB                 | Data at Rest           |
| 4 | Publicly exposed APIs without authentication     | API Security           |
| 5 | No audit logs or session expiration              | Auditing & Session Management |

---

##  Recommended Security Fixes

- **Access Control:** Implement RBAC for doctors, patients, and admins
- **Encryption:**
  - TLS 1.2+ for data in transit
  - AES-256 for data at rest
- **Authentication:**
  - Strong password policies
  - Two-Factor Authentication (2FA)
- **Session Management:**
  - Auto session timeout on inactivity
- **API Security:**
  - Use OAuth 2.0 or API keys with scoped permissions
- **Audit & Logging:**
  - Enable logs for all user activity on health records
- **Backup & Cloud Security:**
  - Encrypted daily backups
  - Fine-grained access control + key rotation

---

##  Legal Compliance References

| Standard | Requirements |
|----------|--------------|
| **HIPAA (USA)** | Access control, encryption, audit logs |
| **DISHA (India)** | Secure handling of e-health records |
| **OWASP Top 10** | Protect against A3 (Data Exposure), A5 (Access Control) |

Useful Links:
- [HIPAA Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/index.html)
- [DISHA Bill – India 2018](https://prsindia.org/billtrack/digital-information-security-health-care-act-2018)

---
