---
source_url: "https://www.palantir.com/docs/foundry/sql-warehousing/compute-usage/"
title: "Compute usage with SQL in Foundry"
---
# Compute usage with SQL in Foundry

Running queries or builds with SQL warehousing in Foundry consumes compute resources, measured in compute-seconds. This page explains how compute is used by the SQL warehouse and how usage is attributed to Foundry resources for reporting. Usage can be viewed from the Resource management application. Foundry compute by query type. The below table lays out Foundry compute used in SQL warehouse queries by query type and links to relevant detailed documentation. Query typeResources queriedQuery engineCompute rate typeResource allocation Read (SELECT). Datasets, Iceberg tables. Furnace. Transforms. Split evenly across resources queried. Write (CREATE, INSERT, UPDATE, DELETE). Datasets, Iceberg tables. Furnace. Transforms. Split evenly across resources written to. Read (SELECT). Datasets, Iceberg tables, virtual tables, restricted views, objects (via materializations). Legacy Spark engine. Contour. Split evenly across resources queried. Read (SELECT). Datasets. Legacy direct read engine. NA. NA. Read (SELECT). Object Types, Many-to-Many Links. Ontology SQL. Foundry Ontology. The underlying saved application executing the query, if not present split evenly across resources queried.
