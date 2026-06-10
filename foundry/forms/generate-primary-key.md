---
source_url: "https://www.palantir.com/docs/foundry/forms/generate-primary-key/"
title: "Generate a primary key"
---
# Generate a primary key

Foundry Forms is no longer the recommended approach for data entry or writeback workflows on Foundry. Instead, build user input workflows with the Foundry Ontology, representing the relevant data structures as object types and configuring the writeback interaction with Actions. Learn more in the Forms overview documentation. A primary key is a value that uniquely identifies each row in a dataset. With Fusion-backed forms, a user can define or automatically generate such a value. Ideally, the field writing to the primary key column should not be editable. Instead, the field should automatically generate a unique value (hidden or otherwise) such as a timestamp or the concatenation of other fields. To set the primary key: With the form configured with at least one field, select the Response data tab. Find the Table columns section at the bottom of the panel. Select the key icon to the right of the desired field. If the primary key field has no value, a unique one will automatically be generated. If the primary key field has a non-unique value, a new row will still be created, but the column will no longer have unique values.
