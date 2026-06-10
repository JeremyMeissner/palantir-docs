---
source_url: "https://www.palantir.com/docs/apollo/apollo-references/apollo-api-documentation/"
parquet_url: "/apollo/apollo-references/apollo-api-documentation/"
title: "Apollo API Explorer"
fetched_at: "2026-05-12T19:34:38.153Z"
---
Apollo API Explorer. Certain Apollo APIs are available directly through GraphQL. GraphQL ↗ is a query language that allows you to precisely fetch the data you want. This is exposed directly in your Apollo Hub through the API Explorer application. The documentation explorer lists all information accessible in your Hub through GraphQL. Documentation. Use the documentation explorer to view all queries and mutations available in the Apollo GraphQL schema. This presents a searchable interface to navigate through the nested schema that branches off the root-level query and mutation type. Examples. The following are introductory examples to get familiar with interacting with Apollo APIs. Getting the current user. 1 2 3 4 5 6 query GetCurrentUser { me { id fullName } } Getting a page of Environments. 1 2 3 4 5 6 7 8 9 query GetEnvironments { apollo { environments(pageSize: 100) { environments { id } } } }
