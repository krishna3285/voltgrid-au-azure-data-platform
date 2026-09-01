# Day 1 interview practice - Azure foundations

## Core questions

### 1. What is a resource group in Azure?

A resource group is a logical container for Azure resources that belong to one solution. It helps organise access control, tags, deployments, and cleanup. For this project, `rg-voltgrid-dev-aue` contains development resources for the VoltGrid platform.

### 2. What is the difference between an Azure subscription and a resource group?

A subscription is the billing and governance boundary. A resource group is an organisational container inside a subscription. One subscription can contain many resource groups.

### 3. Why use ADLS Gen2 for a data engineering project?

ADLS Gen2 provides scalable object storage plus hierarchical folders and data-lake-friendly access controls. It works well with Data Factory, Databricks, Synapse, and Delta Lake for Bronze, Silver, and Gold layers.

### 4. Explain Bronze, Silver, and Gold to a non-technical person.

Bronze is the original delivery box: we keep everything as it arrived. Silver is the checked and organised version. Gold is the ready-to-use business report version.

## Scenario question

### Your Azure trial credit is being used faster than expected. What do you do?

First, open Cost Analysis and identify the resource and meter creating cost. Stop or delete nonessential compute, especially running Databricks clusters or dedicated capacity. Review budgets and alerts, use auto-termination for compute, and avoid provisioned services when serverless or small test runs are sufficient. Never delete storage blindly because it can contain project evidence.

### Follow-up: Does an Azure budget stop resources automatically?

No. Budgets notify you when cost or forecast thresholds are crossed. They are an early-warning mechanism, so operational controls such as auto-termination and manual cleanup are also required.

## Coding and Git question

### Why is `.gitignore` important in an Azure project?

It prevents local secrets, tokens, generated logs, caches, and large temporary files from being added to Git. A public repository must never contain Azure access keys, connection strings, SAS tokens, or passwords.

### Commands to learn

```powershell
git status
git add README.md .gitignore docs
git commit -m "day-01: Azure foundations and storage setup"
```

Run `git status` before every commit. Read the files listed there and ensure no secret or generated file is being committed.

