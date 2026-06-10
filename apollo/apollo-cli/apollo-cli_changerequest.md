---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli/apollo-cli_changerequest/"
title: "Documentation | Apollo CLI > apollo-cli changerequest"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli changerequest

Interact with Apollo change requests

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `-h`, `--help` | Help for changerequest |

### Flags inherited from parent commands

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--apollo-client-id` | Client ID to use for generating Bearer Token |
| `--apollo-client-secret` | Client secret to use for generating Bearer Token |
| `--apollo-token` | Bearer Token to use for authenticated endpoints |
| `--apollo-token-provider` | Specifies how the Bearer Token used for authenticated Apollo endpoint calls is provided. Valid values are "auto", "static", "service-user", or "sso" (default "auto"). If "auto" is specified, the mode is picked from what is configured: "static" if "apollo-token" is set, "service-user" if "apollo-client-id" and "apollo-client-secret" are both set, otherwise "sso" (interactive browser login). Errors if both a bearer token AND (client id OR client secret) are set. If "static" is specified, the token provided by "apollo-token" is used. If "service-user" is specified, "apollo-client-id" and "apollo-client-secret" are used to generate a token from Multipass. If "sso" is specified, an interactive browser-based SSO login against Multipass is used (supports hardware keys like YubiKey); the resulting token is cached per profile and refreshed silently. The login flow is triggered automatically the first time a command needs a token and no valid cached token exists. |
| `--apollo-url` | Base URL for Apollo that is used to derive the API endpoints |
| `--debug` | Enable debug level logging |
| `-e`, `--environment` | Environment ID (including suffix) to use for environment-scoped commands |
| `--http-timeout` | Timeout in minutes for all apollo requests |
| `-k`, `--insecure-skip-verify` | Skip verification of server certificate |
| `-o`, `--output` | Output format (json,yaml,pretty) |
| `--profile` | Use a specific profile from your configuration file |
| `--quiet` | Do not print log output to stderr |
| `--space-id` | Space ID to use for certain space-scoped commands |

### See also

* [apollo-cli](/docs/apollo/apollo-cli/apollo-cli/): CLI to interact with Apollo
* [apollo-cli changerequest approve](/docs/apollo/apollo-cli/apollo-cli_changerequest_approve/): Approve a change request (asynchronously)
* [apollo-cli changerequest cancel](/docs/apollo/apollo-cli/apollo-cli_changerequest_cancel/): Cancel a pending change request
* [apollo-cli changerequest get](/docs/apollo/apollo-cli/apollo-cli_changerequest_get/): Get a change request by RID
* [apollo-cli changerequest list](/docs/apollo/apollo-cli/apollo-cli_changerequest_list/): List change requests
* [apollo-cli changerequest reject](/docs/apollo/apollo-cli/apollo-cli_changerequest_reject/): Reject a change request
* [apollo-cli changerequest reopen](/docs/apollo/apollo-cli/apollo-cli_changerequest_reopen/): Reopen a cancelled or rejected change request
