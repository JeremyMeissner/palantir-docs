---
source_url: "https://www.palantir.com/docs/apollo/managing-environments/"
title: "Documentation | Managing Environments > Overview"
---
# Managing Environments

This section will walk through the workflows related to managing Environments.

The first time you navigate to an [Environment](/docs/apollo/core/environments/) page in Apollo, you will land on the Environment **Overview** tab.
**1. Entities**

This section provides an overview of the upgrade status of the Entities in this Environment. You can view the number of Entities that are up-to-date, in grace period, or blocked. Select a status to view a list of Entities with that status in the **Entities** tab.

**2. README**

This section allows you to add a README to the Environment. You can use this section to provide additional context about the Environment, such as its purpose, location, or any other relevant information. Learn more about [Environment display metadata](/docs/apollo/managing-environments/environment-settings/#display-metadata).

**3. Environment properties**

This section displays general information abut the Environment:

* **Environment RID:** The identifier for the Environment, for example, `ri.apollo.main.environment.aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee`.
* **Last reported state:** The last time the Environment reported back to Apollo.

**4. Plans**

This section displays the latest [Plans](/docs/apollo/core/plans-and-constraints/) that have run on the Environment. You can view the status of each Plan, and when it was initiated. Select a Plan to view more details about it.

**5. Modules**

This section displays the [Modules](/docs/apollo/core/modules/) that are installed in the Environment. You can view the version of each Module. Select a Module to view more details about it.

**6. Artifact Registries**

This section displays the [Artifact Registries](/docs/apollo/managing-artifact-registries/overview/) that are assigned to the Environment and its connection status. Select an Artifact Registry to view more details about it.

**7. Agent connections**

In this section you can view the [Apollo Agents](/docs/apollo/core/agents/) that are deployed in the Environment and the time they last reported to Apollo.

**8. Labels**

You can view all the [labels](/docs/apollo/managing-labels/environment-labels/) that have been applied to this Environment.

**9. Release Channel**

This section displays the default [Release Channel](/docs/apollo/core/release-channels/) that the Environment follows. Note that some Entities in the Environment may follow a different Release Channel.

**10. Roles**

This section displays the [roles](/docs/apollo/core/authorization/#roles-for-environments-and-entities) that have been assigned to Teams for this Environment.

**11. Contact**

This section displays the Environment contact team. If the Environment has additional contact teams, they will also be displayed in this section.

**12. Maintenance windows**

This section displays the [Environment's maintenance windows](/docs/apollo/managing-environments/environment-settings/#environment-and-entity-maintenance-windows). You can view the downtime and no-downtime windows, and their overlap. An Entity may have a different maintenance window based on the [Product maintenance window](/docs/apollo/managing-products/product-maintenance-window/).
