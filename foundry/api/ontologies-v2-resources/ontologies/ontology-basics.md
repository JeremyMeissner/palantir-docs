---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontologies/ontology-basics/"
title: "Ontology basics \u2022 API Reference"
---
Ontologies are categorizations of data into real-world concepts. Those concepts are represented by object types, properties, link types, and action types. Together, these concepts form a descriptive object graph that links together all the key entities in an organization.

For more information, please refer to the [Ontology](/docs/foundry/ontology/overview/) user documentation.

:::callout{theme=neutral title=Note}
Ontology changes are eventually consistent, and it may take few minutes for the API to reflect new Ontologies. 
After adding a new Ontology, the API may return an `OntologyNotFound` error for a few minutes.
:::
