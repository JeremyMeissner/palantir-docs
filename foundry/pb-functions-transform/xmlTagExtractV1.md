---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/xmlTagExtractV1/"
title: "Extract rows from an XML file"
---
# Extract rows from an XML file

Supported in: Batch. Reads a dataset of files and parses each XML file into rows. Transform categories: File. Declared arguments. Dataset: Dataset of files to process. Files. Schema: Schema definition used when parsing the xml files. Type<Struct> XML tag: XML tag that will be used as basis to generate one row per tag. Literal<String> optional Attribute prefix: Prefix for attributes on tags. Literal<String> optional Encoding: The encoding type (character set) of the input file. Enum<ISO_8859_1, US_ASCII, UTF_16, UTF_16BE, UTF_16LE, UTF_8, Windows-31J> optional Value tag: The tag used for the value when there are attributes in the element having no child. Literal<String>
