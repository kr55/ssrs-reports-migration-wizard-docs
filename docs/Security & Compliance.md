---
layout: page
title: Security & Compliance
nav_order: 3
has_children: false
---
# Security & Compliance

SSRS Reports Migration Wizard is designed with **enterprise security, data privacy, and compliance** in mind. All migration operations are performed within your environment, ensuring that data access, execution, and storage remain under your control.

## 🔐 Data Handling & Privacy

- The tool runs **locally on the user’s machine**.
- No report definitions, datasets, data sources, credentials, or subscription data are transmitted outside the customer environment.
- All interactions with SSRS are performed using **official Microsoft SSRS SOAP APIs**.
- No report content or metadata is sent to AzureOps or any external service.

## 📊 Telemetry & Diagnostics

- SSRS Reports Migration Wizard does **not collect or transmit telemetry**.
- No usage statistics, report content, or customer data is tracked.
- License activation communicates only the **minimum information required** for license validation.
- No diagnostic or log data is uploaded automatically.

## 🌐 Offline & Disconnected Environments

- Fully supported in **offline, air-gapped, and disconnected networks**.
- Supports **file-based export and import using SRMW files**, enabling migrations without direct source-to-target connectivity.
- No internet connectivity is required for migration operations after installation and license activation.

## 🔑 Credentials & Secrets Management

- Credentials are **never logged in plain text**.
- The tool allows users to optionally **store credentials for source and target SSRS web service URLs** when the **“Remember credentials”** option is selected.
- Stored credentials are saved **locally on the machine where the tool is installed**.
- Credentials are **not transmitted outside the local machine** and are **never sent to AzureOps or any external service**.
- File share subscription credentials are requested only when required and only when explicitly provided by the user.

### File-Based Migration Credential Handling

- When using the **file-based (SRMW) migration approach**, users may choose to **update data source credentials before exporting to a file**.
- If this option is selected, the updated data source credentials are stored **in plain text within the generated `.srmw` file**.
- This behavior enables seamless import on the target environment but requires appropriate handling of the exported file.

> 🔐 **Security Notice**  
> When exporting SRMW files that contain credentials, customers should:
> - Store files securely
> - Restrict access to authorized personnel only
> - Delete exported files after migration is completed

## 🛡️ Compliance Considerations

- Suitable for environments with **strict data residency and regulatory requirements**.
- No cloud dependency for core migration functionality.
- Execution, access control, and credential handling remain under the customer’s governance.
- Credential storage behavior can be governed by **endpoint security and workstation hardening policies**.

{: .note }
Customers are responsible for ensuring that permissions and credential-handling options selected within the tool align with their internal security policies and compliance standards.

---
