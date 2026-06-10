---
source_url: "https://www.palantir.com/docs/apollo/managing-vulnerabilities/"
title: "Documentation | Managing Vulnerabilities > Overview"
---
# Managing vulnerabilities

:::callout{theme="neutral"}
This is an advanced Apollo feature that is not enabled by default. Contact your Palantir representative to learn more or enable on your Apollo Hub.
:::

Apollo keeps your environments secure by detecting vulnerabilities in your Products and automatically recalling vulnerable Releases. Apollo supports [Trivy ↗](https://trivy.dev/) for vulnerability scanning and [ClamAV ↗](https://www.clamav.net/) for virus scanning. The Apollo risk management workflows provide you full visibility into your security scans and help streamline actions based off of them, as well as streamline communication between developers and security teams on what needs remediation and when, as well as possible exceptions.

After you create a Release, Apollo will automatically run a vulnerability scan for each of the containers that are declared in the [Product manifest](/docs/apollo/apollo-product-specification/manifest/) for the new Release. If you are using the `apollo-cli product-release create` command, Apollo will add the container images declared in your chart default to the Product manifest. The vulnerability scanner requires that all container locators include the full container registry URL and version tag. For example, if you want to scan Postgres from Docker Hub, your Product manifest should include `docker.io/library/postgres:16`.

Apollo will automatically scan:

* All new Releases when they are created.
* All latest Releases and Releases that are installed on Entities. These Releases are scanned by default daily, but you can configure the cadence.

Apollo supports several security related workflows:

* [Vulnerability scanning](/docs/apollo/managing-vulnerabilities/vulnerability-scanning/)
  * [Viewing vulnerabilities and viruses](/docs/apollo/managing-vulnerabilities/vulnerability-scanning/#viewing-vulnerabilities)
  * [Resolve image scan failures](/docs/apollo/managing-vulnerabilities/vulnerability-scanning/#resolve-image-scan-failures)
  * [Automatic recalls based on vulnerabilities](/docs/apollo/managing-vulnerabilities/vulnerability-scanning/#automatic-recalls-based-on-vulnerabilities)
  * [Manually run vulnerability scans](/docs/apollo/managing-vulnerabilities/vulnerability-scanning/#manually-run-vulnerability-scans)
* [Vulnerability suppressions](/docs/apollo/managing-vulnerabilities/vulnerability-suppressions/)
  * [Creating vulnerability suppressions](/docs/apollo/managing-vulnerabilities/vulnerability-suppressions/#creating-vulnerability-suppressions)
  * [Removing vulnerability suppressions](/docs/apollo/managing-vulnerabilities/vulnerability-suppressions/#removing-vulnerability-suppressions)
* [Add security information to promotion evaluation](/docs/apollo/managing-vulnerabilities/promotion-evaluation-security/)
  * [Gate promotion on scans being run](/docs/apollo/managing-vulnerabilities/promotion-evaluation-security/#gate-promotion-on-scans-being-run)
  * [Gate promotion on the results of scans](/docs/apollo/managing-vulnerabilities/promotion-evaluation-security/#gate-promotion-on-the-results-of-scans)
* [Upgrade Entities to CVE-recalled Releases](/docs/apollo/managing-vulnerabilities/cve-recalled-releases-upgrades/)

## Risk scores

Apollo uses the following information to evaluate vulnerabilities:

* [**CVSS Score** ↗](https://nvd.nist.gov/vuln-metrics/cvss): A qualitative measure of severity. There are five possible severities: None, Low, Medium, High, and Critical. Note that Apollo uses CVSS v3.x standards.
* [**EPSS Score** ↗](https://www.first.org/epss/model): An estimate of the probability of the vulnerability being exploited over the next 30 days.
* [**Known Exploit** ↗](https://www.cisa.gov/known-exploited-vulnerabilities-catalog): A catalog maintained by the US government on which vulnerabilities have been observed to be actually exploited in a real-world case.

## Getting started

1. Send the following information to your Palantir representative:

   * Domain for your container registry
   * Your container registry credentials (read-only) so that Apollo can pull containers
   * Whether you want virus scanning as well as vulnerability scanning

2. Navigate to the **Settings & Configuration** page from the main Apollo sidebar and set your desired [permissions for **Vulnerability suppressions** and **Vulnerability SLA settings**](/docs/apollo/core/authorization/#configure-rbac-for-a-resource).

3. If your registry sits behind a firewall you will need to allowlist the Apollo egress IPs.
