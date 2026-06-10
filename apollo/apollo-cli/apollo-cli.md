---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli/apollo-cli/"
title: "Documentation | Apollo CLI > apollo-cli"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli

CLI to interact with Apollo

The Apollo CLI provides a flexible way to interact with Apollo. It can be used to manually publish new Product Releases and as an alternative to the UI for retrieving Apollo metadata (such as which Environments and Products are currently managed by Apollo).

The CLI is supported on Linux, MacOS (Darwin), and Windows.

### Installation

To install the Apollo CLI, follow the instructions provided in the [Apollo CLI getting started guide](/docs/apollo/apollo-getting-started/apollo-cli-getting-started/).

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--apollo-client-id` | Client ID to use for generating Bearer Token |
| `--apollo-client-secret` | Client secret to use for generating Bearer Token |
| `--apollo-token` | Bearer Token to use for authenticated endpoints |
| `--apollo-token-provider` | Specifies how the Bearer Token used for authenticated Apollo endpoint calls is provided. Valid values are "auto", "static", "service-user", or "sso" (default "auto"). If "auto" is specified, the mode is picked from what is configured: "static" if "apollo-token" is set, "service-user" if "apollo-client-id" and "apollo-client-secret" are both set, otherwise "sso" (interactive browser login). Errors if both a bearer token AND (client id OR client secret) are set. If "static" is specified, the token provided by "apollo-token" is used. If "service-user" is specified, "apollo-client-id" and "apollo-client-secret" are used to generate a token from Multipass. If "sso" is specified, an interactive browser-based SSO login against Multipass is used (supports hardware keys like YubiKey); the resulting token is cached per profile and refreshed silently. The login flow is triggered automatically the first time a command needs a token and no valid cached token exists. |
| `--apollo-url` | Base URL for Apollo that is used to derive the API endpoints |
| `--debug` | Enable debug level logging |
| `-e`, `--environment` | Environment ID (including suffix) to use for environment-scoped commands |
| `-h`, `--help` | Help for apollo-cli |
| `--http-timeout` | Timeout in minutes for all apollo requests |
| `-k`, `--insecure-skip-verify` | Skip verification of server certificate |
| `-o`, `--output` | Output format (json,yaml,pretty) |
| `--profile` | Use a specific profile from your configuration file |
| `--quiet` | Do not print log output to stderr |
| `--space-id` | Space ID to use for certain space-scoped commands |

### See also

* [apollo-cli changerequest](/docs/apollo/apollo-cli/apollo-cli_changerequest/): Interact with Apollo change requests
* [apollo-cli configure](/docs/apollo/apollo-cli/apollo-cli_configure/): Updates configuration file that Apollo CLI references to authenticate and interact with Apollo.
* [apollo-cli cve](/docs/apollo/apollo-cli/apollo-cli_cve/): Check product releases for security vulnerabilities
* [apollo-cli entity](/docs/apollo/apollo-cli/apollo-cli_entity/): Manage Apollo entities
* [apollo-cli environment](/docs/apollo/apollo-cli/apollo-cli_environment/): Manage Apollo Environments
* [apollo-cli helm-chart](/docs/apollo/apollo-cli/apollo-cli_helm-chart/): Apollo-specific helm chart utilities
* [apollo-cli module](/docs/apollo/apollo-cli/apollo-cli_module/): Manage Apollo modules
* [apollo-cli product](/docs/apollo/apollo-cli/apollo-cli_product/): Interact with Apollo products
* [apollo-cli product-release](/docs/apollo/apollo-cli/apollo-cli_product-release/): Manage Apollo product releases
* [apollo-cli profile](/docs/apollo/apollo-cli/apollo-cli_profile/): Manage Apollo CLI configuration profiles
* [apollo-cli release-channel](/docs/apollo/apollo-cli/apollo-cli_release-channel/): Manage Apollo Release Channels
* [apollo-cli terminal](/docs/apollo/apollo-cli/apollo-cli_terminal/): Open an interactive terminal in an Apollo environment
