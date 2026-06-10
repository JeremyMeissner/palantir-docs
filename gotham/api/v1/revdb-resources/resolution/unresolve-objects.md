---
source_url: "https://www.palantir.com/docs/gotham/api/v1/revdb-resources/resolution/unresolve-objects/"
title: "Unresolve objects"
---
# Unresolve objects

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Unresolves objects from each other. Path parameters. The primary key of the object to unresolve sub-objects from. Query parameters. The primary key of the constituent objects to unresolve. This list must contain only objects which are sub-objects of the resolved object. It must have at least one object, and may not contain the resolved object. Represents a boolean value that restricts an endpoint to preview mode when set to true. Response body. The primary keys for each of the unresolved objects. The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. Examples.
