---
layout: home
title: Prerequisites
nav_order: 2
has_children: false
---
# Prerequisites

Before using the SSRS Reports Migration Wizard, ensure the following system, network, and access requirements are fulfilled.

## ✅ System Requirements

- **Windows OS** (Windows 10 or above recommended)
- **.NET Framework 4.7.2 or above** installed
- Access to both **source** and **target SSRS report servers**
- SSRS instance version **2012 or later**

## 🌐 Network Prerequisites

- Ensure the SSRS server ports are open (default is **TCP 80** for HTTP).
- Firewalls or proxies should not block access to:
- `http://<servername>/ReportServer`
- `http://<servername>/Reports`

## 🔗 Report Server Access Requirements

🧑‍💼 **Required Roles**
- On the **source server**, your user must have at least the `Browser` role.
- On the **target server**, you need the `Publisher` role or higher.

> If connecting using domain credentials, ensure that:
> - The domain account is trusted on the report server
> - The password is valid and not expired

## 🔐 Granting Access to SSRS Report Server

If your user account is unable to connect or browse the server from the wizard, follow these steps to grant the required permissions:

### On the SSRS Web Portal (Report Manager):

1. Open your browser and navigate to the SSRS Web Portal (e.g.):http://<your-server>/Reports
2. 2. Click on the **gear icon** ⚙️ in the top-right corner and choose **Site Settings**.
3. Under **Security**, select **Add group or user**.
4. Enter your domain user name in this format:DOMAIN\username
5. Assign appropriate role(s):
- `Browser` – minimum required to view reports
- `Publisher` – required to publish/upload reports and data sources
- `Content Manager` – full access (if you’re managing everything)
6. Click **OK** to save.

### On Folder-Level Permissions (if restricted):

1. Navigate to the top-level folder (usually **Home**).
2. Click the **ellipsis (...)** next to the folder > **Manage** > **Security**.
3. Add your domain user again and assign the necessary role(s).
🔄 If inheritance is broken, ensure you set permissions for **each subfolder** as well.


## Next Step

Once all prerequisites are met, proceed to the [Getting Started Guide](./getting-started.md) to begin your migration.

