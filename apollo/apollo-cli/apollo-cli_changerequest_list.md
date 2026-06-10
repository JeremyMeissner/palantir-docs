---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli/apollo-cli_changerequest_list/"
title: "Documentation | Apollo CLI > apollo-cli changerequest list"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli changerequest list

List change requests

List change requests with optional filters.

Valid status values: PENDING\_APPROVALS, APPROVED, REJECTED, CANCELLED, ERROR, APPROVED\_APPLYING, APPROVED\_MERGED

```bash
apollo-cli changerequest list [flags]
```

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--author` | Filter by author user ID |
| `--environment` | Filter by environment ID |
| `-h`, `--help` | Help for list |
| `--limit` | Maximum number of results to return |
| `--space-id` | Space ID (required) |
| `--status` | Filter by status (e.g., PENDING\_APPROVALS, APPROVED, REJECTED, CANCELLED) |
| `--title` | Filter by title |

### Flags inherited from parent commands

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--apollo-client-id` | Client ID to use for generating Bearer Token |
| `--apollo-client-secret` | Client secret to use for generating Bearer Token |
| `--apollo-token` | Bearer Token to use for authenticated endpoints |
| `--apollo-token-provider` | Specifies how the Bearer Token used for authenticated Apollo endpoint calls is provided. Valid values are "auto", "static", "service-user", or "sso" (default "auto"). If "auto" is specified, the mode is picked from what is configured: "static" if "apollo-token" is set, "service-user" if "apollo-client-id" and "apollo-client-secret" are both set, otherwise "sso" (interactive browser login). Errors if both a bearer token AND (client id OR client secret) are set. If "static" is specified, the token provided by "apollo-token" is used. If "service-user" is specified, "apollo-client-id" and "apollo-client-secret" are used to generate a token from Multipass. If "sso" is specified, an interactive browser-based SSO login against Multipass is used (supports hardware keys like YubiKey); the resulting token is cached per profile and refreshed silently. The login flow is triggered automatically the first time a command needs a token and no valid cached token exists. |
| `--apollo-url` | Base URL for Apollo that is used to derive the API endpoints |
| `--debug` | Enable debug level logging |
| `--http-timeout` | Timeout in minutes for all apollo requests |
| `-k`, `--insecure-skip-verify` | Skip verification of server certificate |
| `-o`, `--output` | Output format (json,yaml,pretty) |
| `--profile` | Use a specific profile from your configuration file |
| `--quiet` | Do not print log output to stderr |

### See also

* [apollo-cli changerequest](/docs/apollo/apollo-cli/apollo-cli_changerequest/): Interact with Apollo change requests
