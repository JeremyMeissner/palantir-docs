---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/hubspot/"
title: "Hubspot"
---
# Hubspot

Connect Foundry to HubSpot to import data and create, modify, and delete records in HubSpot. Source configuration. Before you configure the HubSpot connection, generate a HubSpot API key. You can get an existing API key or generate a new HubSpot API key by following the steps below. In your Hubspot account, select the settings icon in the main navigation bar. In the left sidebar menu, navigate to Integrations > API Key. If a key has never been generated for your account, select Generate API Key. If an API key already exists, select Show to view it. You can now set the retrieved key in the api-key connection property. The following is the most basic structure for a Hubspot connection: 1 2 3 type: hubspot config: apiKey: '{{api-key}}'
