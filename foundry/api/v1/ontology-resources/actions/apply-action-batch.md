---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/actions/apply-action-batch/"
parquet_url: "/foundry/api/v1/ontology-resources/actions/apply-action-batch/"
title: "Apply Action Batch"
fetched_at: "2026-05-12T19:34:37.514Z"
---
Apply Action Batch. Applies multiple actions (of the same Action Type) using the given parameters. Changes to objects or links stored in Object Storage V1 are eventually consistent and may take some time to be visible. Edits to objects or links in Object Storage V2 will be visible immediately after the action completes. Up to 20 actions may be applied in one call. Actions that only modify objects in Object Storage v2 and do not call Functions may receive a higher limit. Note that parameter default values and notifications are not currently supported by this endpoint. Third-party applications using this endpoint via OAuth2 must request the following operation scopes: api:ontologies-read api:ontologies-write. Path parameters. The unique Resource Identifier (RID) of the Ontology that contains the action. To look up your Ontology RID, please use the List ontologies endpoint or check the Ontology Manager. The API name of the action to apply. To find the API name for your action, use the List action types endpoint or check the Ontology Manager. Request body. Response body. Success response. Examples.
