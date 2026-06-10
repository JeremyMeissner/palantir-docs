---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli-deprecated/apollo-cli_publish_asset/"
title: "Documentation | Apollo CLI [Deprecated] > apollo-cli publish asset [Deprecated]"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli publish asset \[Deprecated]

:::callout{theme="warning"}
This command is [Deprecated](/docs/apollo/apollo-references/developer-api-limited-support-policies/).
This command is deprecated and will be removed in December 2025. Use [apollo-cli product-release asset publish](/docs/apollo/apollo-cli/apollo-cli_product-release_asset_publish/) instead.
:::

Creates and publishes an asset product TGZ to Apollo.

Creates an asset product TGZ with the provided Maven coordinate. The asset subdirectory contents are taken from the specified local directory. The command then publishes both the asset TGZ and its product release to Apollo using the specified publisher parameters.

```bash
apollo-cli publish asset [flags]
```

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--asset-path` | File or directory to include in the published asset |
| `-h`, `--help` | Help for asset |
| `--images` | Container image URIs that enable Apollo to know which images it needs to check for availability before recommending an upgrade to a containerized entity. |
| `--label-name` | Name of the label added to the product release |
| `--label-value` | Value of the label added the product release |
| `--manifest-extension` | Name of the manifest extension |
| `--manifest-extension-key` | Key of the provided manifest extension |
| `--manifest-extension-value` | Value of the provided manifest extension |
| `--manifest-file` | Manifest file |
| `--maven-coordinate` | Maven coordinate for product |

### Flags inherited from parent commands

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--apollo-client-id` | Client ID to use for generating Bearer Token |
| `--apollo-client-secret` | Client secret to use for generating Bearer Token |
| `--apollo-token` | Bearer Token to use for authenticated endpoints |
| `--apollo-token-provider` | Specifies how the Bearer Token used for authenticated Apollo endpoint calls is provided. Valid values are "auto", "static", or "service-user" (default "auto"). If "auto" is specified, will use either the Bearer Token provided by "apollo-token" or a Bearer Token obtained by using "apollo-client-id" and "apollo-client-secret" to generate a token from Multipass depending on which values are set (but will error if both values are set). If "static" is specified, the token provided by "apollo-token" is used. If "service-user" is specified, "apollo-client-id" and "apollo-client-secret" are used to generate a token from Multipass. |
| `--apollo-url` | Base URL for Apollo that is used to derive the API endpoints |
| `--debug` | Enable debug level logging |
| `--dry-run` | Print the operations that would be performed |
| `-e`, `--environment` | Environment ID (including suffix) to use for environment-scoped commands |
| `--http-timeout` | Timeout in minutes for all apollo requests |
| `-k`, `--insecure-skip-verify` | Skip verification of server certificate |
| `-o`, `--output` | Output format (json,yaml,pretty) |
| `--profile` | Use a specific profile from your configuration file |
| `--quiet` | Do not print log output to stderr |
| `--space-id` | Space ID to use for certain space-scoped commands |

### See also

* [apollo-cli publish](/docs/apollo/apollo-cli-deprecated/apollo-cli_publish/): Publishes a product to Apollo
