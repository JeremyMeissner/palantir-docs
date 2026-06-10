---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/getTimestampsForSceneFramesV1/"
title: "Get timestamps for scene frames"
---
# Get timestamps for scene frames

Supported in: Batch. Get the timestamps and scene scores for detected scene frame transitions in the video. Expression categories: Media. Declared arguments. Media reference: The video from which scene frame timestamps are extracted. Expression<Media reference> optional Scene sensitivity: Controls how easily scene changes are detected. Higher sensitivity detects more subtle transitions. Enum<Less sensitive, More sensitive, Standard> Output type: Array<Struct<timestamp, scene_score>>
