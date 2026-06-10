---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isValidMediaReferenceV1/"
parquet_url: "/foundry/pb-functions-expression/isValidMediaReferenceV1/"
title: "Is valid media reference"
fetched_at: "2026-05-12T19:34:36.603Z"
---
Is valid media reference. Supported in: Batch, Faster, Streaming. Returns true if the input is a valid Foundry media reference. Expression categories: Boolean. Declared arguments. Expression: String representing a media reference. Expression<String> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: mediaRef. mediaRefOutput {"mimeType":"PDF","reference":{"type":"datasetFile","datasetFile":{"fileReference":{"datasetRid":"ri.foundry.main.dataset.a","ref":"master","logicalFilePath":"file.pdf"}}}} true. {"mimeType":"PDF","reference":{"type":"mediaSetItem","mediaSetItem":{"mediaSetRid":"ri.mio.main.media-set.a", "mediaItemRid":"ri.mio.main.media-item.a"}}} true. not a media reference. false.
