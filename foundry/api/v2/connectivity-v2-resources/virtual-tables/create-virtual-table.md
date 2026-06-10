---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/virtual-tables/create-virtual-table/"
title: "Create Virtual Table"
---
# Create Virtual Table

Creates a new Virtual Table from an upstream table. The VirtualTable will be created in the specified parent folder and can be queried through Foundry's data access APIs. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-virtual-table-write. Path parameters. The Resource Identifier (RID) of a Connection (also known as a source). Request body. The unique resource identifier (RID) of a Folder. The name of a VirtualTable. Response body. The created VirtualTable. The Resource Identifier (RID) of a registered VirtualTable. The name of a VirtualTable. The unique resource identifier (RID) of a Folder. Examples. Error responses.
