---
source_url: "https://www.palantir.com/docs/foundry/foundryts/foundryts/"
parquet_url: "/foundry/foundryts/foundryts/"
title: "foundryts.FoundryTS"
fetched_at: "2026-05-12T19:34:36.017Z"
---
foundryts.FoundryTS. class foundryts.FoundryTS(*args, **kwargs). The singleton that sends queries to the FoundryTS backend under the hood. This singleton is automatically initialized using environment variables and the user is not required to initialize an instance for calling FoundryTS supported functions. Examples. 1 >>> fts = FoundryTS(). property search. Property for searching the Ontology with foundryts.search.Search. We recommend using this property to perform search as it enforces safeguards for the searching in the Foundry ecosystem. Examples. 1 2 3 >>> fts = FoundryTS() >>> objects = fts.search.series(metadata.property == 'value') NodeCollection(...).
