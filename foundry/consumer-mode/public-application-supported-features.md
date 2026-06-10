---
source_url: "https://www.palantir.com/docs/foundry/consumer-mode/public-application-supported-features/"
title: "Documentation | Public Applications > Currently supported features"
---
# Currently supported features

You can call a limited set of ontology operations from a [Public Application](/docs/foundry/consumer-mode/public-application-overview/). While the currently supported set of operations is intentionally small, the list of supported operations will expand as broader observability and rate-limit controls are released.

## Supported operations

The following ontology operations are callable from a Public Application:

| Operation | Description | Restrictions |
| --- | --- | --- |
| [Get Ontology full metadata](/docs/foundry/api/v2/ontologies-v2-resources/ontologies/get-ontology-full-metadata/) | Retrieves the full metadata of the ontology, including object types, link types, action types, queries, and interfaces. | None. |
| Load Ontology metadata | Retrieves the metadata for a specific subset of the ontology specified in the request body. | None. |
| [Apply Action](/docs/foundry/api/v2/ontologies-v2-resources/actions/apply-action/) | Applies an action with the provided parameters and writes the result to the ontology. | Function-backed actions are blocked. Neither batch action application nor webhooks are supported. |
| [Load Object Set](/docs/foundry/api/v2/ontologies-v2-resources/ontology-object-sets/load-object-set/) | Loads ontology objects from a provided object set definition. Supports loading many objects, a single object by primary key, and a linked object. | `SearchAround`, `FilteredObjectSets`, and `orderBy` clauses are not supported. |

## Not currently supported

The following features are explicitly **not** callable from a Public Application:

* All function executions, including queries, function-backed actions, and function-backed batch actions.
* Aggregations and search, including `searchObjects` and `aggregateObjects`.
* Complex search-arounds and [derived properties](/docs/foundry/ontology/derived-properties/).
* Interfaces in your ontology.
* Attachments, both upload and download.
* Media, both upload and download.
* Time series streaming endpoints, including `streamAllPoints` and `streamValues`.

Additionally, you cannot call any non-ontology platform APIs, such as those used for platform administration, model creation, schedule orchestration, or chatbot interactions, from a Public Application.

## Why these limits exist

Every endpoint a Public Application exposes is reachable by anyone who meets the application's ingress policies, which can be as broad as the open internet. The supported set is restricted to operations whose cost is bounded and whose data shape is predictable, ensuring abuse on the public surface cannot cause unbounded compute spend or exfiltrate unintended data.

Function-driven workflows are excluded for the same reason: a malicious user could construct expensive queries against your enrollment's compute resources. If your workflow requires heavier processing on data submitted through a Public Application, perform that processing asynchronously inside Foundry. As an example, you can configure a non-function-backed action to write the submission, then use [Automate](/docs/foundry/automate/overview/) to react to the new objects on a controlled cadence.

## Exceptions and future development

If your workflow depends on operations outside the supported set, contact Palantir Support. Exceptions are evaluated case by case, and any exception still requires use case approval from an **Information Security Officer** in your enrollment before enablement. The supported set will grow as the platform releases:

* Per-application compute observability to detect abuse early.
* Stronger rate-limiting controls beyond the current per-application limits.

The roadmap is intentionally conservative: a Public Application is the first place an enrollment's data and compute can be reached without a Foundry account, so the platform only enables additional functionality when the protections necessary to keep that surface safe are in place.
