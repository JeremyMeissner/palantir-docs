---
source_url: "https://www.palantir.com/docs/foundry/upgrade-assistant/impacted-resources/"
parquet_url: "/foundry/upgrade-assistant/impacted-resources/"
title: "Identifying impacted resources"
fetched_at: "2026-05-12T19:34:37.814Z"
---
Identifying impacted resources. Before announcing a platform change, Palantir writes telemetry that identifies any potentially impacted resource. For example, before announcing the platform's deprecation of Python 2 in favor of Python 3, Palantir identified all repositories still using Python 2 and made the list of repositories available in Upgrade Assistant. Most of the telemetry powering Upgrade Assistant is implemented as a background task, so it is not updated in real time. Taking the Python 2 deprecation as an example: if you upgraded one of the repositories to Python 3 in preparation for the Python 2 deprecation, you would need to wait up to 24 hours for the repository to show as compliant in Upgrade Assistant. Additionally, because each platform change is different, there is no standard way to identify potentially-impacted resources. However, changes announced in Upgrade Assistant may contain details about the telemetry in their description.
