---
source_url: "https://www.palantir.com/docs/foundry/code-repositories/recall-artifact/"
parquet_url: "/foundry/code-repositories/recall-artifact/"
title: "Recall an Artifact"
fetched_at: "2026-05-12T19:34:36.075Z"
---
Recall an Artifact. It is possible to recall Conda Artifacts to stop downstream consumers from compiling code with the recalled version. We recommend having patch versions available for recalled Artifacts before starting the recall process. Follow these steps to recall an Artifact: Search for the Conda Artifact in your Artifact Repository and select it to view the Version History section in the summary page. Select the version to recall and then choose Recall. A Recall artifacts pop-up will appear. Enter the reason for recalling the Artifact in the field. View the Version History again to see that the Artifact is now marked as Recalled. Unrecall. You can unrecall an Artifact. To unrecall an Artifact, select the version of a recalled Artifact and click Unrecall. Delete. Conda Artifacts can be recalled, but it is not possible to delete any Artifacts in an Artifact repository. If you explicitly need to delete an Artifact, you must delete the Artifact repository.
