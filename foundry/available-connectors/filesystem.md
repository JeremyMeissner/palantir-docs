---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/filesystem/"
title: "Agent-level filesystem"
---
# Agent-level filesystem

Files stored on disk on an agent can be synced into Foundry using the filesystem source type. This source type can be used to sync data from a Network File System ↗ (NFS) or Network-attached storage ↗ (NAS) to Foundry, by mounting the NFS or NAS on the agent host and configuring the root directory appropriately. Supported capabilities. CapabilityStatus Exploration. 🟢 Generally available. Bulk import. 🟢 Generally available. Incremental. 🟢 Generally available. File exports. 🟢 Generally available. Configuration. ParameterRequired?DefaultDescription rootDirectory. Y. Root directory containing data. fileMustNotChangeDuration. N. PT2.0S. Amount of time (in ISO-8601 ↗) a file must remain constant before being considered for upload. Note: If possible, use the more efficient lastModifiedBefore processor. Example: 1 2 3 myDirectorySource: type: directory rootDirectory: /foo/bar. Data Connection excludes all symbolic links, regardless of whether the links are to files or to folders.
