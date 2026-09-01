# Day 1 runbook - Azure account and lake storage setup

## Before you create anything

1. Sign in to the Azure portal.
2. In the search bar, type `Subscriptions` and open it.
3. Confirm that the selected subscription is your Azure free trial. Do not create resources in a subscription you do not recognise.

## Part A - Create a cost budget

1. Search for `Cost Management + Billing`.
2. Open **Cost Management** and select **Budgets**.
3. Select **Add**.
4. Scope: choose the free-trial subscription.
5. Name: `budget-voltgrid-30day`.
6. Reset period: Monthly.
7. Amount: `150` in your billing currency.
8. Set actual-cost email alerts at 25%, 50%, 75%, 90%, and 100%.
9. Add your email address and select **Create**.

> A budget sends alerts; it does not turn off resources. Check Cost Analysis daily once Databricks or other compute has been created.

## Part B - Create a resource group

1. Search for `Resource groups` and choose **Create**.
2. Subscription: select your Azure free trial.
3. Resource group: `rg-voltgrid-dev-aue`.
4. Region: select **Australia East** when available. If it is unavailable, use a nearby supported region and record the choice in the README.
5. Select **Review + create**, then **Create**.

## Part C - Create ADLS Gen2

1. Search for `Storage accounts` and select **Create**.
2. Resource group: `rg-voltgrid-dev-aue`.
3. Storage account name: `stvoltgrid` followed by 8 lowercase letters or digits. The name must be globally unique, 3-24 characters, and contain only lowercase letters and numbers.
4. Region: use the same region as the resource group.
5. Performance: **Standard**. Redundancy: **Locally-redundant storage (LRS)**.
6. In the **Advanced** tab, enable **Hierarchical namespace**. This makes the account ADLS Gen2.
7. Leave public anonymous access disabled. Do not change networking defaults today.
8. Select **Review + create**, then **Create**. Wait for deployment to finish.

## Part D - Create containers

1. Open the new storage account.
2. In the left menu, select **Data storage** then **Containers**.
3. Select **+ Container** six times and create the following lowercase names:

```text
bronze
silver
gold
quarantine
checkpoints
config
```

Keep the public access level set to **Private** for each one.

## Stop point

Take one screenshot showing the six containers, save it as `screenshots/day-01-storage-containers.png`, then tell your instructor whether every checkbox in the Day 1 learning file is complete.
