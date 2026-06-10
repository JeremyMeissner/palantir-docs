---
source_url: "https://www.palantir.com/docs/apollo/managing-entities/report-entities/"
parquet_url: "/apollo/managing-entities/report-entities/"
title: "Reporting Entities"
fetched_at: "2026-05-12T19:34:38.151Z"
---
Reporting Entities. Apollo provides the ability to track the state of deployed Entities across your Spoke Environments. Entities added through the method described in Adding Entities are referred to as “managed" Entities. Non-managed Entities can also be tracked and reported through Apollo. The Apollo CLI command add-unmanaged-service [MavenCoordinate] --environment=[env-id] --stack=[stack] --service=[service-id] can be run with the coordinates of the deployed software to add it as a non-managed Entity or update an existing one. The Entity will then show up as an Entity in the Apollo Control Center, along with the deployed version at the time the CLI command was run. Since the Entity is not managed by Apollo, the deployed version in the Apollo Control Center will not automatically update to reflect newly deployed versions of the software. We recommend setting up a process that can scan the non-managed Entities and report their latest versions to Apollo. This process can be set up to run on a schedule and report the latest versions via the CLI. This will ensure that the displayed version in the Apollo Control Center is not falling behind.
