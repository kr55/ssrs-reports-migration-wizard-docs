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






