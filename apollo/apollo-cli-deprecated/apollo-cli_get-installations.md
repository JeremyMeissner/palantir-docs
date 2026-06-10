---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli-deprecated/apollo-cli_get-installations/"
title: "Documentation | Apollo CLI [Deprecated] > apollo-cli get-installations [Deprecated]"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli get-installations \[Deprecated]

:::callout{theme="warning"}
This command is [Deprecated](/docs/apollo/apollo-references/developer-api-limited-support-policies/).
This command is deprecated and will be removed in December 2025.Use [apollo-cli entity list](/docs/apollo/apollo-cli/apollo-cli_entity_list/) instead.
:::

Gets the installations for the specified environment(s)

```bash
apollo-cli get-installations [flags]
```

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--environment` | Environments |
| `-h`, `--help` | Help for get-installations |

### Flags inherited from parent commands

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--apollo-client-id` | Client ID to use for generating Bearer Token |
| `--apollo-client-secret` | Client secret to use for generating Bearer Token |
| `--apollo-token` | Bearer Token to use for authenticated endpoints |
| `--apollo-token-provider` | Specifies how the Bearer Token used for authenticated Apollo endpoint calls is provided. Valid values are "auto", "static", or "service-user" (default "auto"). If "auto" is specified, will use either the Bearer Token provided by "apollo-token" or a Bearer Token obtained by using "apollo-client-id" and "apollo-client-secret" to generate a token from Multipass depending on which values are set (but will error if both values are set). If "static" is specified, the token provided by "apollo-token" is used. If "service-user" is specified, "apollo-client-id" and "apollo-client-secret" are used to generate a token from Multipass. |
| `--apollo-url` | Base URL for Apollo that is used to derive the API endpoints |
| `--debug` | Enable debug level logging |
| `--http-timeout` | Timeout in minutes for all apollo requests |
| `-k`, `--insecure-skip-verify` | Skip verification of server certificate |
| `-o`, `--output` | Output format (json,yaml,pretty) |
| `--profile` | Use a specific profile from your configuration file |
| `--quiet` | Do not print log output to stderr |
| `--space-id` | Space ID to use for certain space-scoped commands |
