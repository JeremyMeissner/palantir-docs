---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/connections/get-configuration-connections-batch/"
parquet_url: "/foundry/api/v2/connectivity-v2-resources/connections/get-configuration-connections-batch/"
title: "Get Configuration Connections Batch"
fetched_at: "2026-05-12T19:34:37.674Z"
---
Get Configuration Connections Batch. Returns a map of Connection RIDs to their corresponding configurations. Connections are filtered from the response if they don't exist or the requesting token lacks the required permissions. The maximum batch size for this endpoint is 200. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-connection-read. Request body. Response body. Examples.
