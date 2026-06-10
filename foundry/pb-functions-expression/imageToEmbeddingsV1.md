---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/imageToEmbeddingsV1/"
title: "Image to embeddings"
---
# Image to embeddings

Supported in: Batch. Converts images into embeddings using the provided model. Expression categories: Media. Declared arguments. Media reference: Column containing media references (images) to convert to embeddings. Expression<Media reference> Model: The embedding model to use for the conversion. Must support vision capabilities. Model. optional Output mode: Choose between simply returning the output or returning a struct, containing either the output in a field named 'ok', or any errors in a field named 'errors'. Enum<Simple, With errors> Output type: Embedded vector. Examples. Example 1: Base case. Description: Example embeddings for an image. Argument values: Media reference: mediaRef. Model: googleSiglip2Embedding( ). Output mode: null. mediaRefOutput { "mimeType": "image/jpeg", "reference": { "type": "mediaSetViewItem", "... embeddings-result. Example 2: Null case. Description: Null input should have a null output. Argument values: Media reference: mediaRef. Model: googleSiglip2Embedding( ). Output mode: null. mediaRefOutput null. null.
