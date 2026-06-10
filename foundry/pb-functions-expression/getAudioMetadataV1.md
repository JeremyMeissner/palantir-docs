---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/getAudioMetadataV1/"
parquet_url: "/foundry/pb-functions-expression/getAudioMetadataV1/"
title: "Extract audio metadata"
fetched_at: "2026-05-12T19:34:36.572Z"
---
Extract audio metadata. Supported in: Batch. Extracts metadata fields from an audio file. Expression categories: Media. Declared arguments. Media reference: The column containing media references to audio files in the media set. Expression<Media reference> Metadata to include: Select the metadata fields to include in the output. Set<Enum<Audio specification, Bytes, Format>> Output type: Struct. Examples. Example 1: Base case. Argument values: Media reference: Media Reference. Metadata to include: [Format, Specification, Bytes] Media ReferenceOutput {"mimeType":"audio","reference":{"type":"mediaSetItem","mediaSetItem":{"mediaSetRid":"ri.mio.test.media-set.1","mediaItemRid":"ri.mio.test.media-item.1"}}} { bytes: 156700, format: audio, specification: { **b...
