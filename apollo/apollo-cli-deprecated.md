---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli-deprecated/"
title: "Documentation | Apollo CLI [Deprecated] > apollo-cli add-unmanaged-service [Deprecated]"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli add-unmanaged-service \[Deprecated]

:::callout{theme="warning"}
This command is [Deprecated](/docs/apollo/apollo-references/developer-api-limited-support-policies/).
This command is deprecated and will be removed in October 2025. Adding unmanaged services is not a recommended practice. Add managed services instead using [apollo-cli entity install](/docs/apollo/apollo-cli/apollo-cli_entity_install/).
:::

Registers an unmanaged service in Apollo

```bash
apollo-cli add-unmanaged-service [flags]
```

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--dry-run` | Print the operations that would be performed |
| `-e`, `--environment` | Environment |
| `-h`, `--help` | Help for add-unmanaged-service |
| `--maven-coordinate` | Maven coordinate for the artifact |
| `--service` | Service |
| `--stack` | Stack |

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
