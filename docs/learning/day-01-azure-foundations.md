# Day 1 - Azure foundations

## Goal

Create a safe Azure home for VoltGrid data and understand the five basic Azure concepts used throughout this project.

## The five ideas

| Term | Plain-English meaning | VoltGrid example |
|---|---|---|
| Subscription | The account boundary that holds billing and permissions. | The free Azure trial with its credit. |
| Resource group | A labelled folder for related Azure resources. | `rg-voltgrid-dev-aue`. |
| Region | The Azure geography where a resource is created. | Australia East. |
| Storage account | The Azure service that owns cloud file storage. | `stvoltgrid<unique>`. |
| Container | A top-level folder inside a storage account. | `bronze`, `silver`, or `gold`. |

## Why ADLS Gen2?

Azure Data Lake Storage Gen2 is Azure Blob Storage with a hierarchical file system. Data engineering tools can efficiently read folders and files, and access can be managed at the folder level. It is where our raw, cleaned, and reporting-ready data will live.

## Medallion layers

```text
Source data -> Bronze -> Silver -> Gold
                 raw       trusted    reporting-ready
```

- Bronze stores what arrived, with minimal change.
- Silver validates, cleans, standardises, and deduplicates it.
- Gold contains business tables, KPIs, facts, and dimensions.

## Verification checklist

- [ ] A subscription budget exists with email alerts.
- [ ] The resource group `rg-voltgrid-dev-aue` exists.
- [ ] The storage account has Hierarchical namespace enabled.
- [ ] Six containers exist: bronze, silver, gold, quarantine, checkpoints, config.
- [ ] No storage access key has been copied into this repository.
