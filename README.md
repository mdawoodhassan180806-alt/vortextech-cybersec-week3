# Vortex Tech — Week 3 Cyber Security Internship: Basic Security Audit

## Overview
This repository contains my Week 3 (Intermediate) submission for the Vortex Tech Cyber Security Internship Track: a structured, beginner-level security audit of **OWASP Juice Shop**, an intentionally vulnerable web application built for security training.

The audit covers three vulnerability categories:
1. **Reflected Cross-Site Scripting (XSS)** — in the product search field
2. **Broken Authentication** — user enumeration via login error messages
3. **Sensitive Data Exposure** — sensitive fields returned in a REST API response

Full details, evidence (screenshots), and remediation recommendations are in [`Week3_Security_Audit_Report.docx`](./Week3_Security_Audit_Report.docx).

## ⚠️ Scope & Legal Notice
All testing was performed **only** against a local instance of OWASP Juice Shop, a deliberately vulnerable practice application designed for this exact purpose. No production systems or third-party websites were tested. Do not use these techniques against any system you do not own or have explicit written permission to test.

## How to Run the Target Locally

**Prerequisite:** [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running.

```bash
# Pull the OWASP Juice Shop image
docker pull bkimminich/juice-shop

# Run it, mapping container port 3000 to your local machine
docker run -d -p 3000:3000 bkimminich/juice-shop
```

Then open your browser to **http://localhost:3000**.

> Alternative: if Docker isn't available, use the official OWASP Juice Shop online demo instance (search "OWASP Juice Shop online demo").

## Tools Used
- **Browser DevTools** (Network tab) — for inspecting requests/responses and manual XSS testing
- **[OWASP ZAP](https://www.zaproxy.org/)** — for automated vulnerability scanning of the local instance

## Repository Contents
| File | Description |
|---|---|
| `Week3_Security_Audit_Report.docx` | Full audit report: methodology, findings, evidence, and remediation steps |
| `README.md` | This file |

## Methodology Summary
1. Explored the app manually, testing input fields for XSS with payloads such as `<script>alert(1)</script>`
2. Tested the login flow with valid/invalid credentials to check for information-leaking error messages
3. Used DevTools' Network tab to inspect API responses for improperly exposed sensitive data
4. Ran an OWASP ZAP automated scan against the local instance and reviewed the report
5. Documented each finding with category, evidence, impact, and remediation

## Disclaimer
This project was completed for educational purposes as part of a cybersecurity internship curriculum. It is intended to demonstrate security auditing methodology on a legal, purpose-built vulnerable application only.
