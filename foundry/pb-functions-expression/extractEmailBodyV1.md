---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/extractEmailBodyV1/"
parquet_url: "/foundry/pb-functions-expression/extractEmailBodyV1/"
title: "Extract email body"
fetched_at: "2026-05-12T19:34:36.684Z"
---
Extract email body. Supported in: Batch. Extracts the email body from an email media item as either plain text or html. Expression categories: Media. Declared arguments. Media reference: The email media item to extract the body from. Expression<Media reference> optional Error handling: Determines the behavior of the pipeline for inputs that fail to process. Enum<FAIL, NULL> optional Output format: The format to return the extracted email body as. Defaults to plain text. Enum<HTML, Plain Text> Output type: String.
