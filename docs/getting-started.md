---
layout: page
title: Getting started
permalink: /getting-started/
nav_order: 4
---

# Getting started
{: .no_toc }

## Step 1: Select the Source

<img src="../media/1-select-source.png" style="width:100%; height:100%">

- Choose the **source type**: either an SSRS Report Server or an SRMW file.
- Enter the **Report Server URI** (e.g., `http://localhost/ReportServer`).
- Select the **authentication method**:
  - Use Current Domain Credentials
  - Use Specified Domain Credentials (provide domain\username and password)

Click **Next** to proceed.

---

## Step 2: Select the Target

<img src="../media/2-select-target.png" style="width:100%; height:100%">

- Choose the **target type**: another SSRS Report Server or SRMW file.
- Enter the **target server URI**.
- Provide authentication details as needed.

Click **Next** to continue.

---

## Step 3: Select SSRS Items to Migrate

<img src="../media/3-select-report-items.png" style="width:100%; height:100%">

- Browse and select specific SSRS objects (folders, reports, datasets, data sources).
- The tool displays a **tree view** of your SSRS folder hierarchy.
- You can preview object counts by type on the right panel.
- Optionally, check **"Migrate standard subscriptions"** to include subscriptions.

Click **Next** once you’ve selected the required items.

---

## Step 4: Review and Confirm

<img src="../media/4-review.png" style="width:100%; height:100%">

- Review the source and target server details.
- A detailed list of items to be updated will be shown.
- The summary includes folder and item-level actions.

Click **Finish** to start the migration process.

---

## Step 5: Migration Summary

<img src="../media/5-finish.png" style="width:100%; height:100%">

- View a detailed log of all migrated items.
- Warnings about existing folders or skipped operations will be shown.
- Click **Report** to view a full migration log or **Close** to exit the wizard.

---

## Next Steps

You’re now ready to migrate your SSRS environments more easily and efficiently using the SSRS Reports Migration Wizard. For advanced usage and troubleshooting, refer to the [Documentation](#).

