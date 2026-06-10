---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli-deprecated/apollo-cli_manifest_verify/"
title: "Documentation | Apollo CLI [Deprecated] > apollo-cli manifest verify [Deprecated]"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli manifest verify \[Deprecated]

:::callout{theme="warning"}
This command is [Deprecated](/docs/apollo/apollo-references/developer-api-limited-support-policies/).
This command is deprecated and will be removed in December 2025. Use [apollo-cli product-release verify](/docs/apollo/apollo-cli/apollo-cli_product-release_verify/) instead.
:::

Verifies that the specified manifest is valid

Verifies that the specified manifest is valid. If the specified file has the extension ".tgz" or ".tar.gz"
then the file at \*/deployment/manifest.yml is verifies; otherwise, the file is verified directly.

```bash
apollo-cli manifest verify [flags]
```

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `-h`, `--help` | Help for verify |
| `--manifest-source-file` | Path to file with the manifest to verify (manifest file or product TGZ that contains manifest) |
| `--print-manifest` | Prints the YAML representation of the manifest |

### Flags inherited from parent commands

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--apollo-client-id` | Client ID to use for generating Bearer Token |
| `--apollo-client-secret` | Client secret to use for generating Bearer Token |
| `--apollo-token` | Bearer Token to use for authenticated endpoints |
| `--apollo-token-provider` | Specifies how the Bearer Token used for authenticated Apollo endpoint calls is provided. Valid values are "auto", "static", or "service-user" (default "auto"). If "auto" is specified, will use either the Bearer Token provided by "apollo-token" or a Bearer Token obtained by using "apollo-client-id" and "apollo-client-secret" to generate a token from Multipass depending on which values are set (but will error if both values are set). If "static" is specified, the token provided by "apollo-token" is used. If "service-user" is specified, "apollo-client-id" and "apollo-client-secret" are used to generate a token from Multipass. |
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

* [apollo-cli manifest](/docs/apollo/apollo-cli-deprecated/apollo-cli_manifest/): Commands to create or verify a manifest for Apollo
