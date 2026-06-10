---
source_url: "https://www.palantir.com/docs/apollo/recalling-releases/"
title: "Documentation | Recalling Releases > Overview"
---
# Overview

**Recalls** are how you communicate to Apollo that there is a problem with one or more Releases. You can use recalls to move Entities off bad Releases and prevent Apollo from upgrading Modules or Entities to these Releases.

Releases can be recalled [manually](/docs/apollo/recalling-releases/recall-release/) or automatically due to [instability measured in promotion pipelines](/docs/apollo/managing-products/tracking-product-releases/#recalled-status) or using an API by an external service such as container vulnerability scanning.

After one or more Releases are recalled, Apollo will automatically remediate the issue by blocking the Release(s) from further roll-out and prioritize deploying other non-recalled Releases to affected Entities according to the recall's [**roll-off strategy**](/docs/apollo/recalling-releases/roll-off-strategies/).

Apollo can also be configured to upgrade Entities directly to a CVE-recalled Release when doing so improves their security posture. See [Upgrade Entities to CVE-recalled Releases](/docs/apollo/managing-vulnerabilities/cve-recalled-releases-upgrades/).

You can view the list of recalls and their roll-off status along with completed and reverted recalls in the **Recalls** tab of a Product or Module overview.
You can view the recalls that affect a specific Release by navigating to the **Releases** tab and hovering over the **Status** column for the Release.
A banner is displayed on a Release's home page when it is affected by an active recall. Selecting **Details** will open details about each active recall such as the recall range, who issued the recall, and why the recall was issued.

You can also view the recalls for a specific Release by selecting that Release from the table and then selecting **Details** from the banner on the Release's home page.
We recommend recalling a Release as soon as an issue is discovered to prevent the issue from being deployed to more Environments. Once an investigation into the issue is completed, you can [edit](/docs/apollo/recalling-releases/recall-release/#edit-a-recall) or [revert](/docs/apollo/recalling-releases/recall-release/#revert-a-recall) the recall.
