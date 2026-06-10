---
source_url: "https://www.palantir.com/docs/foundry/api/v2/notepad-v2-resources/generation-jobs/generation-job-basics/"
parquet_url: "/foundry/api/v2/notepad-v2-resources/generation-jobs/generation-job-basics/"
title: "Generation Job basics"
fetched_at: "2026-05-12T19:34:37.697Z"
---
Generation Job basics. GenerationJobs are used to generate content from templates. After creating a GenerationJob, the client should monitor job status by getting the GenerationJob and inspecting the 'status' property. If a GenerationJob succeeds, the client can save the generated content as a new Document or export it via an ExportJob. GenerationJobs are temporary resources intended for immediate use after creation; they must be used within one hour. If a GenerationJob cannot be found after one hour, it may have been deleted automatically.
