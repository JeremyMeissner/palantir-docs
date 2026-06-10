---
source_url: "https://www.palantir.com/docs/apollo/apollo-cli-deprecated/apollo-cli_publish_helm-chart/"
title: "Documentation | Apollo CLI [Deprecated] > apollo-cli publish helm-chart [Deprecated]"
---
<!-- This file is auto-generated in the apollo-cli repo by ./godelw generate. Do not update manually! -->

# apollo-cli publish helm-chart \[Deprecated]

:::callout{theme="warning"}
This command is [Deprecated](/docs/apollo/apollo-references/developer-api-limited-support-policies/).
This command is deprecated and will be removed in December 2025. Use [apollo-cli product-release helm-chart init](/docs/apollo/apollo-cli/apollo-cli_product-release_helm-chart_init/) to generate the manifest, and then use [apollo-cli product-release create](/docs/apollo/apollo-cli/apollo-cli_product-release_create/) to publish the product to Apollo.
:::

Publishes a helm-chart product to Apollo

```bash
apollo-cli publish helm-chart [flags]
```

### Flags

| Flag                      | Use                      |
| ------------------------- | ------------------------ |
| `--chart-file` | Path to local Helm chart |
| `--helm-ca-file` | Helm pull: verify certificates of HTTPS-enabled servers using this CA bundle |
| `--helm-cert-file` | Helm pull: identify HTTPS client using this SSL certificate file |
| `--helm-chart-name` | Helm chart name. If the chart resides in a remote OCI repository, this must be the full OCI URL (e.g. oci://repo/chartName) |
| `--helm-chart-version` | Helm chart version |
| `--helm-key-file` | Helm pull: identify HTTPS client using this SSL key file |
| `--helm-manifest-extension-rollout-strategy` | Rollout strategy manifest extension: valid values are 'manageRollout' (default) and 'applyChangesNoWait' |
| `--helm-pass-credentials` | Helm pull: pass credentials to all domains |
| `--helm-password` | Helm pull: chart repository password where to locate the requested chart |
| `--helm-repository-url` | Helm repository URL |
| `--helm-username` | Helm pull: chart repository username where to locate the requested chart |
| `--helm-values` | Helm template: Specify values in a YAML file.  Note that values are only used to render chart templates locally.  Default configs will need to be added in Apollo before installation. |
| `-h`, `--help` | Help for helm-chart |
| `--maven-coordinate` | Maven coordinate for product |
| `--release-channel` | Release channels (defaults to RELEASE if not specified) |
| `--validate` | Runs static validation on the supplied helm chart before publishing |

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
