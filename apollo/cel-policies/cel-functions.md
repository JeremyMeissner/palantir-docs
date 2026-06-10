---
source_url: "https://www.palantir.com/docs/apollo/cel-policies/cel-functions/"
title: "Documentation | CEL policies specification > Response types"
---
# Response types

CEL policy expressions use two categories of functions:

* Result function: Returns a policy outcome
* Predicate function: Returns a Boolean value used to branch between outcomes

Every policy expression must return a result function on every code path.

## Result functions

### `approve(reason)`

Auto-approves the change without requiring any reviewer. The reason is recorded in the audit log.

```
approve("Trusted environment import from source-of-truth.")
```

### `reject(reason)`

Rejects the change immediately. A rejected change cannot be applied until it is edited and resubmitted.

```
reject("Replica count cannot exceed 10.")
```

### `no_op()`

Signals that this policy has no opinion on the change. The result is discarded and other enabled policies continue to be evaluated normally.

Use `no_op()` as the default branch in policies that are only intended to apply to specific change types or Entity types. See [Examples](/docs/apollo/cel-policies/examples/) for patterns that use `no_op()` as a fallback.

### `require_role(rid, roleId, reason)`

Requires a user who holds a specific role on the given resource to approve the change. It takes the following parameters:

* `rid`: The resource identifier of the resource. Obtain this from `referencedResources.key.rid`.
* `roleId`: The role identifier, such as `"entity:operator"` or `"environment:admin"`.
* `reason`: A message describing why this approval is required.

```
require_role(referencedResources.installation.rid, "entity:operator", "Entity config changes require operator approval.")
```

### `require_operation(rid, operation, reason)`

Requires a user who holds a specific operation permission (editor, approver, administrator, or operator depending on the policy) on the given resource to approve the change. It takes the following parameters:

* `rid`: The resource identifier of the resource.
* `operation`: The operation string, such as `"entity:approve-config-update"`.
* `reason`: A message describing why this approval is required.

```
require_operation(referencedResources.installation.rid, "entity:approve-config-update", "Entity operators must approve config updates.")
```

### `require_team(teamName, reason)`

Requires review from the named Apollo team. It takes the following parameters:

* `teamName`: The name of the Apollo team.
* `reason`: A message describing why this team's approval is required.

```
require_team("platform-security", "Security team must approve network configuration changes.")
```

### `require_any(requirements, reason)`

Satisfied when any one of the provided requirements is met. This allows OR semantics among a set of reviewer requirements. Each element in `requirements` must be a call to `require_role`, `require_operation`, or `require_team`. It takes the following parameters:

* `requirements`: A list of reviewer requirements.
* `reason`: A message describing the combined requirement.

```
require_any([
  require_role(referencedResources.installation.rid, "entity:operator", "Entity operators may approve."),
  require_team("platform-oncall", "The on-call team may approve.")
], "Either an entity operator or the on-call team must approve.")
```

## Predicate functions

Predicate functions return a Boolean and are used as conditions in ternary expressions. They do not produce a policy result on their own.

### `should_auto_approve_service_user(type, author, onBehalfOf, editors)`

Returns `true` if the change was made by a trusted first-party Apollo service account that is auto-approved for the given change type, and no one else has edited the change request since it was opened.

This function encodes the list of trusted Apollo service accounts and the change types each account is approved for. It is intended for use in default policies to ensure that automated Apollo workflows do not require manual approval.

:::callout{theme="warning"}
The default policies include a call to `should_auto_approve_service_user` for each supported change type. Removing or modifying this call can break automated Apollo workflows that depend on auto-approval.
:::

```
should_auto_approve_service_user(type, author, onBehalfOf, editors)
  ? approve("Authored by a trusted first-party service user.")
  : require_role(referencedResources.installation.rid, "entity:operator", "Operator approval required.")
```

### `is_author_service_user(username, author, onBehalfOf, editors)`

Returns `true` if the given username matches the change request author or the `onBehalfOf` user, the matching user is a service account, and no one other than that user has edited the change request since it was opened. It takes one additional parameter beyond the standard input fields:

* `username`: The service account username to check against.

Use this function when you want to auto-approve changes made by a specific named service account. For checking trusted first-party Apollo service accounts, prefer `should_auto_approve_service_user`.

```
is_author_service_user("svc-deploy", author, onBehalfOf, editors)
  ? approve("Trusted deployment service account.")
  : require_role(referencedResources.installation.rid, "entity:operator", "Operator approval required.")
```

### `is_trusted_module_request(author, metadata, editors)`

Returns `true` if the change request was opened by the Apollo Module deployment service, carries Module installation metadata, and has not been edited by any other user since it was opened.

```
is_trusted_module_request(author, metadata, editors)
  ? approve("Trusted module request.")
  : no_op()
```

### `is_trusted_import_request(author, metadata, editors)`

Returns `true` if the change request was opened by the Apollo deployment state service, carries the Environment import metadata flag, and has not been edited by any other user since it was opened.

Environment imports represent a sync from a source-of-truth Environment and are considered trusted changes.

```
is_trusted_import_request(author, metadata, editors)
  ? approve("Trusted environment import from source-of-truth.")
  : no_op()
```
