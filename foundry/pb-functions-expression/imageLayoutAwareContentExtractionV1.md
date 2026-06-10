---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/imageLayoutAwareContentExtractionV1/"
title: "Extract layout-aware content from images"
---
# Extract layout-aware content from images

Supported in: Batch, Faster. Extracts content from images, while preserving the original layout. Expression categories: Media. Declared arguments. Languages to detect: Languages to detect in the input files. Set<Enum<Afrikaans, Albanian, Amharic, Arabic, Armenian, Assamese, Azerbaijani, Azerbaijani - Cyrilic, Basque, Belarusian, and more ...>> Media reference: The image to extract content from. Expression<Media reference> Output format: Output will be a string. Enum<Full extract, Text and tables> optional Error handling: Determines the behavior of the pipeline for inputs that fail to process. Enum<FAIL, NULL> Output type: Array<Struct<block_index, block_id, block_type, content, bounding_box, languages<String>, confidence>> | String. Examples. Example 1: Base case. Argument values: Languages to detect: {ENG} Media reference: mediaReference. Output format: TEXT. Error handling: FAIL_FAST. mediaReferenceOutput {"mimeType":"image/png","reference":{"type":"mediaSetItem","mediaSetItem":{"mediaSetRid":"ri.mio.main.media-set.a", "mediaItemRid":"ri.mio.main.media-item.a"}}} extracted content.
