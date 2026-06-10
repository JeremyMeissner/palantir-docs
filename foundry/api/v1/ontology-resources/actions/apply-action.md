---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/actions/apply-action/"
parquet_url: "/foundry/api/v1/ontology-resources/actions/apply-action/"
title: "Apply Action"
fetched_at: "2026-05-12T19:34:37.516Z"
---
Apply Action. Applies an action using the given parameters. Changes to objects or links stored in Object Storage V1 are eventually consistent and may take some time to be visible. Edits to objects or links in Object Storage V2 will be visible immediately after the action completes. Note that parameter default values are not currently supported by this endpoint. Third-party applications using this endpoint via OAuth2 must request the following operation scopes: api:ontologies-read api:ontologies-write. Path parameters. The unique Resource Identifier (RID) of the Ontology that contains the action. To look up your Ontology RID, please use the List ontologies endpoint or check the Ontology Manager. The API name of the action to apply. To find the API name for your action, use the List action types endpoint or check the Ontology Manager. Request body. Response body. Success response. Examples.
