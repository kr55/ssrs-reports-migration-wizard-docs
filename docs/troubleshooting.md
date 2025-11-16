---
layout: page
title: Troubleshooting guide
permalink: /troubleshooting/
nav_order: 5
---

# Troubleshooting Guide

---

## 1. Issue: Data-Driven Subscriptions Fail to Import

During the migration or import process, data-driven subscriptions may fail to be created successfully, often presenting errors related to data source connectivity.

### **Typical Causes**

The import failure usually stems from the target **SQL Server Reporting Services (SSRS)** instance being unable to establish a successful connection to the underlying data sources defined in the report.

Key reasons include:

* **Missing or Incorrect Database Client:** The target server lacks a required database client (e.g., **Oracle Managed Driver**) for the data source type.
* **Invalid Connection Information:**
    * The **connection identifier** is missing or invalid.
    * The **connection string** in the data source is not valid for the target environment.
* **Credential Issues:**
    * **Credentials** for the data source were not supplied or are incorrect on the target server.
    * The report uses credentials that are **not stored credentials** (e.g., Windows Integrated Security when not configured correctly).
* **Target Server Configuration:**
    * The data source was **not configured properly** during the migration.
    * The **SQL Server Agent Job** is not running (which is required for subscription processing).

### **Resolution**

The primary resolution is to ensure **correct and complete data source configuration** on the target SSRS server.

1.  **Verify Data Source Properties:** During a server-to-server migration or a server-to-file import, ensure you correctly configure all data source properties and credentials on the **Manage Connection Properties** screen of the Migration Wizard.
2.  **Confirm Target Connectivity:** Validate that the target SSRS server has the necessary drivers/clients and network access to connect to all report data sources using the configured connection strings and credentials. **Stored credentials** are generally recommended for subscriptions.
3.  **Check SQL Agent:** Confirm that the **SQL Server Agent** service is running on the target SQL Server instance that hosts the ReportServer database, as it's vital for scheduling and executing subscriptions.

### **Summary**

Data-driven subscription import failures fundamentally occur because of **missing or incorrect data source configurations** on the target SSRS server. By verifying the required database clients, ensuring valid connection strings, and correctly supplying **stored credentials** for the data sources, you allow the migration tool to successfully create the data-driven subscriptions.

---

## 2. Issue: The user data source credentials do not meet the requirements to run this report or shared dataset

**Error message:** The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credentials are not stored in the report server database, or the user data source is configured not to require credentials but the unattended execution account is not specified.

### **Typical Causes**

This failure typically occurs when a report or shared dataset is executed without a valid security context that the Reporting Services service can use to connect to the data source. This is common during migrations where Windows Integrated Security used by the original author isn't properly translated, or when subscriptions attempt to run reports that require user input credentials.

Key reasons include:

* **Missing Stored Credentials:** The data source connection is configured to use credentials supplied by the user (or Windows Authentication) which are **not valid** when running background processes like subscriptions or cached report snapshots.
* **Unattended Execution Account Not Set:** The data source is configured for **No Credentials** or **Windows Integrated Security**, but the Report Server is missing the **Unattended Execution Account** configuration needed to impersonate a service account for data retrieval.
* **Encrypted Credentials Issue:** Credentials were not successfully re-encrypted or migrated to the target Report Server environment, rendering the stored credentials invalid.
* **Account Permissions:** The stored account has valid credentials but **lacks necessary database permissions** on the target data source.

### **Resolution**

The resolution depends on your organization's security policy for report execution. You must ensure the report has a valid, non-interactive security context for the Report Server to use.

1.  **Configure Stored Credentials:** For the specific report data source(s) or shared datasets, switch the connection type to **Credentials stored securely in the report server**.
    * Enter a **valid domain user account** and password that has read access to the underlying database. This is the most common fix for subscriptions and data-driven tasks.
2.  **Use Unattended Execution Account:** If the data source must use **Windows Integrated Security** or **No Credentials**:
    * Ensure the **Report Server Configuration Manager** has a valid **Unattended Execution Account** specified under the "Execution Account" settings. This account must have necessary permissions on the data source.
3.  **Validate Report Execution:** If the report uses multiple data sources, verify that *all* data sources referenced are configured with a stored or execution account credential.
4.  **Database Permissions Check:** Verify that the account being used (either the **Stored Credentials** account or the **Unattended Execution Account**) has the correct `SELECT` and `EXECUTE` permissions on the source database.

### **Summary**

This error is a security-related failure indicating that the **SSRS service cannot connect to the data source** using the configured method (Stored, Integrated, or None) because a valid, non-interactive security token is missing or invalid. Configuring **Stored Credentials** for the data source is the most reliable way to resolve this issue during a migration.
