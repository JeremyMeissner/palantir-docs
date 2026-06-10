---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/pdfTableOfContentsV1/"
title: "Extract table of contents from PDF"
---
# Extract table of contents from PDF

Supported in: Batch, Faster. Produces a table of contents from a PDF based on the headings used within the document. Expression categories: Media. Declared arguments. Media reference: The column containing media references to PDF files in a media set. Expression<Media reference> Output type: Array<Struct<level, title, page>> Examples. Example 1: Base case. Argument values: Media reference: Media Reference. Media ReferenceOutput {"mimeType":"application/pdf","reference":{"type":"mediaSetItem","mediaSetItem":{"mediaSetRid":"ri.mio.test.media-set.1","mediaItemRid":"ri.mio.test.media-item.1"}}} [ { level: 0, page: 2, title: Chapter 1, }, { **l...
