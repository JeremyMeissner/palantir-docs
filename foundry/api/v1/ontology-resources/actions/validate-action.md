---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/actions/validate-action/"
title: "Validate Action"
---
# Validate Action

Validates if an action can be run with the given set of parameters. The response contains the evaluation of parameters and submission criteria that determine if the request is VALID or INVALID. For performance reasons, validations will not consider existing objects or other data in Foundry. For example, the uniqueness of a primary key or the existence of a user ID will not be checked. Note that parameter default values are not currently supported by this endpoint. Unspecified parameters will be given a default value of null. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The unique Resource Identifier (RID) of the Ontology that contains the action. To look up your Ontology RID, please use the List ontologies endpoint or check the Ontology Manager. The API name of the action to validate. To find the API name for your action, use the List action types endpoint or check the Ontology Manager. Request body. Response body. Success response. Represents the state of a validation. Enum values: VALID, INVALID. Examples.
