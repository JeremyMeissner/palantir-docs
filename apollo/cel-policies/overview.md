---
source_url: "https://www.palantir.com/docs/apollo/cel-policies/overview/"
title: "Documentation | CEL policies specification > Overview"
---
# CEL policies

Apollo uses Common Expression Language (CEL) policies to determine who must approve a change request before it can be applied. When a change request is opened, Apollo evaluates all enabled policies for the space and uses the results to set reviewer requirements.

## Evaluation model

Policies run at the level of individual Entity changes, not at the level of the change request as a whole. A change request that modifies two Entities produces two separate policy evaluations and can produce different reviewer requirements for each.

All enabled policies are evaluated against each input. The reviewer requirements they produce are combined with AND semantics, meaning every requirement from every policy must be satisfied before a change can be approved.

If a policy does not apply to a given change, it must return `no_op()`. This signals that the policy has no opinion on that change and its result is discarded. Other policies continue to be evaluated normally. If all enabled policies return `no_op()` for a given change, Apollo returns an error.

## Policy structure

A policy consists of:

* An **expression string** that must return a result such as `approve()`, `reject()`, `no_op()`, or `require_role()`. See [Response types](/docs/apollo/cel-policies/cel-functions/) for the full list.
* Optional **named variables**, each defined with a name, type, and value. Variables are referenced in the expression using `{{ policyVariable.variableName }}` placeholders, which are replaced with the configured value before evaluation. This allows administrators to configure a policy without modifying its expression.

## Input fields

The following fields are available in every policy expression.

| Field | Type | Description |
|-------|------|-------------|
| `type` | string | The change type, such as `CREATE_ENTITY` or `UPDATE_ENTITY`. See [Change type API reference](/docs/apollo/cel-policies/input-types/). |
| `author` | object | The user who opened the change request. Has `username` (string) and `teams` (set of strings) fields. |
| `onBehalfOf` | object | Present when a service account opens the change request on behalf of another user. In this case, `author` contains the service account and `onBehalfOf` contains the actual requester. Same structure as `author`. Absent otherwise. |
| `editors` | set | The usernames of users who edited the change request after it was opened. Each entry is a string. |
| `request` | object | A normalized representation of the entity being changed. Contains `apolloEntityType`, `apolloEntityId`, and `releaseChannel`. |
| `diff` | map | A sparse map of fields that changed. Only changed fields are present; removed fields have value `"<<unset>>"`. |
| `referencedResources` | map | Resources associated with the change, keyed by resource name. Available keys depend on the change type. See [Change type API reference](/docs/apollo/cel-policies/input-types/). |

## Example

The following policy auto-approves entity config updates from a configurable list of trusted authors and requires operator approval for all other authors. The list is defined as a variable so it can be maintained without modifying the expression:

```yaml
id: trusted-author-approval-policy
displayName: "Trusted Author Approval Policy"
variables:
  - name: trustedAuthors
    type: STRING_LIST
    description: Human authors whose changes do not require additional approval
    value:
      - "alice"
      - "bob"
definition: |
  type == "UPDATE_ENTITY" ? (
    author.username in {{ policyVariable.trustedAuthors }}
      ? approve("Change authored by a trusted team member.")
      : require_role(referencedResources.installation.rid, "entity:operator", "Operator approval required.")
  ) : no_op()
```

For more examples, see [Examples](/docs/apollo/cel-policies/examples/).
