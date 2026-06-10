---
source_url: "https://www.palantir.com/docs/apollo/cel-policies/input-types/"
title: "Documentation | CEL policies specification > Change type API reference"
---
# Change type API reference

Every CEL policy evaluation receives a `type` field indicating the kind of change being evaluated. The `type` value determines what keys are available in `referencedResources`. Use `type` to guard a policy so it only runs for the change types it is designed to handle.

:::callout{theme="neutral"}
For a Entity change that is part of a Module installation, `referencedResources` also includes `module` and `moduleRelease` keys for the associated Module, in addition to the keys listed below.
:::

## Entity changes

### `CREATE_ENTITY`

Triggered when an Entity is added to an Environment.

**Available `referencedResources` keys:** `environment`

### `UPDATE_ENTITY`

Triggered when an Entity's application configuration is modified.

**Available `referencedResources` keys:** `environment`, `installation`, `product` (if the Entity has a Product assigned)

### `UPDATE_ENTITY_SETTINGS`

Triggered when an Entity's operational settings are modified, such as its Release Channel. Also produced when an Entity is marked for deletion.

**Available `referencedResources` keys:** `environment`, `installation`, `product` (if the Entity has a Product assigned)

### `DELETE_ENTITY`

Triggered when an Entity is removed from the deployment configuration.

**Available `referencedResources` keys:** `environment`, `installation`, `product` (if the Entity has a Product assigned)

## Entity maintenance windows

### `SET_ENTITY_MAINTENANCE_WINDOWS`

Triggered when maintenance windows are set on a standard Entity type such as a service or daemon.

**Available `referencedResources` keys:** `environment`, `installation`, `product` (if applicable)

### `REMOVE_ENTITY_MAINTENANCE_WINDOWS`

Triggered when maintenance windows are removed from a standard Entity type.

**Available `referencedResources` keys:** `environment`, `installation`, `product` (if applicable)

### `CREATE_ENTITY_MAINTENANCE_WINDOW_OVERRIDE`

Triggered when a maintenance window override is created for a standard Entity type.

**Available `referencedResources` keys:** `environment`, `installation`, `product` (if applicable)

### `SET_GENERIC_ENTITY_MAINTENANCE_WINDOWS`

Triggered when maintenance windows are set on a generic Entity type such as a network security configuration.

**Available `referencedResources` keys:** `environment`, `installation`

### `REMOVE_GENERIC_ENTITY_MAINTENANCE_WINDOWS`

Triggered when maintenance windows are removed from a generic Entity type.

**Available `referencedResources` keys:** `environment`, `installation`

### `CREATE_GENERIC_ENTITY_MAINTENANCE_WINDOW_OVERRIDE`

Triggered when a maintenance window override is created for a generic Entity type.

**Available `referencedResources` keys:** `environment`, `installation`

## Environment changes

### `UPDATE_ENVIRONMENT_SETTINGS`

Triggered when Environment-level settings are modified, such as the default Release Channel.

**Available `referencedResources` keys:** `environment`

### `UPDATE_ENVIRONMENT_CONFIG`

Triggered when the Environment configuration file is modified.

**Available `referencedResources` keys:** `environment`

### `UPDATE_EXTERNAL_DEPENDENCIES`

Triggered when external dependency configuration is modified.

**Available `referencedResources` keys:** `environment`

### `UPDATE_ENVIRONMENT_PROPERTIES`

Triggered when Environment metadata is modified, such as the display name or description.

**Available `referencedResources` keys:** `environment`

### `CREATE_ENVIRONMENT`

Triggered when a new Environment is created.

**Available `referencedResources` keys:** None

### `DELETE_ENVIRONMENT`

Triggered when an Environment is deleted.

**Available `referencedResources` keys:** `environment`

### `EXIT_BOOTSTRAP_MODE`

Triggered when an Environment exits bootstrap mode.

**Available `referencedResources` keys:** `environment`

## Space settings

### `MODIFY_SPACE_SETTINGS`

Triggered when space-level settings are modified.

**Available `referencedResources` keys:** Varies by setting; keyed by the resource being changed.

### `MODIFY_RESOURCE_OVERRIDE_SPACE_SETTINGS`

Triggered when resource-level overrides for space settings are modified.

**Available `referencedResources` keys:** Varies by setting; keyed by the resource being changed.

## Pipeline changes

### `CREATE_PIPELINE`

Triggered when a new pipeline is created.

**Available `referencedResources` keys:** `pipelineRoot`

### `UPDATE_PIPELINE`

Triggered when an existing pipeline's settings are modified.

**Available `referencedResources` keys:** `bundlingPipeline`

### `UPDATE_PIPELINE_TRANSFER_TARGET`

Triggered when a pipeline's transfer target connections are modified. Also produced alongside `CREATE_PIPELINE` for each connected transfer target.

**Available `referencedResources` keys:** `transferTarget`

### `DELETE_PIPELINE`

Triggered when a pipeline is deleted.

**Available `referencedResources` keys:** `bundlingPipeline`

### `ARCHIVE_PIPELINE`

Triggered when a pipeline is archived.

**Available `referencedResources` keys:** `bundlingPipeline`

### `UNARCHIVE_PIPELINE`

Triggered when a pipeline is unarchived.

**Available `referencedResources` keys:** `bundlingPipeline`

## Team changes

### `CREATE_TEAM`

Triggered when a new team is created.

**Available `referencedResources` keys:** `teamRoot`

### `UPDATE_TEAM`

Triggered when a team's membership or settings are modified.

**Available `referencedResources` keys:** `team`

### `DELETE_TEAM`

Triggered when a team is deleted.

**Available `referencedResources` keys:** `team`

## Product settings

### `CREATE_PRODUCT_SETTINGS`

Triggered when Product settings are created for a Product.

**Available `referencedResources` keys:** `product`

### `UPDATE_PRODUCT_SETTINGS`

Triggered when existing Product settings are modified.

**Available `referencedResources` keys:** `product`

### `DELETE_PRODUCT_SETTINGS`

Triggered when Product settings are deleted.

**Available `referencedResources` keys:** `product`

## Security changes

### `CREATE_EGRESS_POLICIES`

Triggered when egress policies are created.

**Available `referencedResources` keys:** `egressPolicyRoot`

### `DELETE_EGRESS_POLICIES`

Triggered when egress policies are deleted.

**Available `referencedResources` keys:** `egressPolicyRoot`

### `CREATE_TERMINAL_ACCESS_GRANT`

Triggered when a terminal access grant is created.

**Available `referencedResources` keys:** `environment`

### `MODIFY_VULNERABILITY_SUPPRESSIONS`

Triggered when vulnerability suppressions are added or modified.

**Available `referencedResources` keys:** `vulnerabilitySuppression`

### `REMOVE_VULNERABILITY_SUPPRESSIONS`

Triggered when vulnerability suppressions are removed.

**Available `referencedResources` keys:** `vulnerabilitySuppression`

## Management overrides

### `CREATE_MANAGEMENT_OVERRIDE`

Triggered when a management override is created.

**Available `referencedResources` keys:** None

### `UPDATE_MANAGEMENT_OVERRIDE`

Triggered when a management override is modified.

**Available `referencedResources` keys:** None

### `DELETE_MANAGEMENT_OVERRIDE`

Triggered when a management override is deleted.

**Available `referencedResources` keys:** None
