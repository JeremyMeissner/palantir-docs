---
source_url: "https://www.palantir.com/docs/foundry/object-indexing/overview/"
parquet_url: "/foundry/object-indexing/overview/"
title: "Indexing"
fetched_at: "2026-05-12T19:34:37.490Z"
---
Indexing. In the Ontology, indexing is the process of making tabular or other forms of data in Foundry datasources available for faster data retrieval operations through specialized databases. This section of documentation describes the indexing process for Object Storage V2, in which indexing is overseen by the Object Data Funnel service ("Funnel"). The Funnel service is responsible for orchestrating Funnel pipelines that create and modify object instances in the Ontology and ensure up-to-date data and metadata. There are two main types of funnel pipelines, funnel batch pipelines and funnel streaming pipelines, which allow users to adopt one or the other indexing mechanism depending on their datasource landscape, latency and workflow requirements, and cost considerations. Learn more about Funnel batch pipelines. Learn more about Funnel streaming pipelines. For information about Object Storage V1 (Phonograph) indexing, review the legacy documentation.
