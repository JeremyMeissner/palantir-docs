---
source_url: "https://www.palantir.com/docs/apollo/cel-policies/examples/"
title: "Documentation | CEL policies specification > Examples"
---
# Examples

## Auto-approve a trusted service account with fallback

A common pattern is to auto-approve changes made by a specific service account and require human approval otherwise. Use `is_author_service_user` to check whether the author or `onBehalfOf` user matches a named service account:

```
is_author_service_user("svc-deploy", author, onBehalfOf, editors)
  ? approve("Trusted deployment service account.")
  : require_role(referencedResources.installation.rid, "entity:operator", "Operator approval required.")
```

To auto-approve changes made by any trusted first-party Apollo service account rather than a specific one, use `should_auto_approve_service_user` instead. This function is used in the default policies and encodes the list of Apollo-managed service accounts. See the `should_auto_approve_service_user` entry in [Response types](/docs/apollo/cel-policies/cel-functions/) before modifying or removing it from a default policy.

## Require a specific team for a specific Entity type

To write a policy that only applies to a particular Entity type, guard on `request.apolloEntityType` and return `no_op()` for anything else:

```
request.apolloEntityType == "network-security"
  ? require_team("platform-security", "Security team must approve network configuration changes.")
  : no_op()
```

This policy produces a reviewer requirement only for `network-security` Entities. For all other entity types, it returns `no_op()` and Apollo moves on to the next policy.

## Auto-approve installing a specific Module

For changes that are part of a Module installation, `referencedResources` includes a `module` key. Use `referencedResources.module.name` to check which Module is being installed and auto-approve installations of a trusted module:

```
"module" in referencedResources && referencedResources.module.name == "my-trusted-module"
  ? approve("Approved installation of my-trusted-module.")
  : no_op()
```

The guard on `"module" in referencedResources` ensures this expression only matches changes that are part of a single-Module installation. For change requests involving more than one Module, the `module` key is not populated.

## Gate on a field change using `diff`

Use the `diff` field to apply reviewer requirements only when a specific field has changed. Fields are only present in `diff` if they were modified:

```
type == "UPDATE_ENTITY" && "replicas" in diff
  ? require_role(referencedResources.installation.rid, "entity:operator", "Replica count changes require operator approval.")
  : no_op()
```

This policy only fires when the `replicas` field is part of the change. Other updates to the same Entity pass through without triggering this requirement.
