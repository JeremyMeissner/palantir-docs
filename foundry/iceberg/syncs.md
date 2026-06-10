---
source_url: "https://www.palantir.com/docs/foundry/iceberg/syncs/"
title: "Documentation | Iceberg tables > Data Connection syncs"
---
# Syncing data to Iceberg tables from Data Connection

:::callout{theme="neutral" title="Beta"}
Syncs into Iceberg tables are in the [beta](/docs/foundry/platform-overview/development-life-cycle/) phase of development.
:::

You can use [Data Connection](/docs/foundry/data-connection/overview/) to sync data from supported external sources directly into Foundry Iceberg tables.
## Supported sources

Currently supported source types are:

* [Custom JDBC](/docs/foundry/available-connectors/custom-jdbc-sources/)
* [Microsoft SQL Server](/docs/foundry/available-connectors/microsoft-sql-server/)
* [Oracle](/docs/foundry/available-connectors/oracle/)
* [PostgreSQL](/docs/foundry/available-connectors/postgresql/)
* [Snowflake](/docs/foundry/available-connectors/snowflake/)

:::callout{theme="neutral"}
Iceberg syncs are only supported on the [Foundry worker](/docs/foundry/data-connection/architecture/#foundry-worker-with-direct-connection-policies) runtime. When ingesting data from a private network, configuring [agent proxy egress policies](/docs/foundry/administration/configure-egress/#agent-proxy-egress-policies) is recommended.
:::

## Write modes

Foundry offers both non-incremental and incremental [batch syncs](/docs/foundry/data-connection/set-up-sync/) into Iceberg for these source types. You can create new Iceberg syncs from the source overview page.

When configuring your sync, you can choose between the following write mode options:

* **"Overwrite" write mode:** Overwrites all rows in the Iceberg table with new data, producing an `overwrite` Iceberg snapshot.
* **"Append" write mode:** Appends new rows to the Iceberg table, while retaining all existing data, producing an `append` Iceberg snapshot.
* **"Update" write mode:** Updates existing rows in the Iceberg table which match on a primary key identifier column, inserting new rows for previously unseen identifiers. This produces an `overwrite` Iceberg snapshot, overwriting only the affected data files.

More customized incremental ingests are also supported using wildcard-based custom SQL statement. See the [incremental syncs documentation](/docs/foundry/data-connection/optimize-jdbc-syncs/#incremental-syncs) for more detail.

:::callout{theme="warning"}
Schema evolution on Iceberg syncs is not supported. This means that re-running a sync after modifying the schema of the source table will fail. Consider creating a new sync on the updated table schema in these circumstances.
:::
