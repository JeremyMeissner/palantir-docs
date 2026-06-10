---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/parseKmlFilesV1/"
title: "Parse KML files into geometry lists"
---
# Parse KML files into geometry lists

Supported in: Batch. Parses each raw KML file into a list of typed geometries. Transform categories: File. Declared arguments. Dataset: Dataset of files to process. Files. optional Should prepare: Flag indicating whether to prepare the geometry for Ontology ingest after parsing. You should always prepare unless know that your input is invalid and still want to perform geospatial operations on it. Default to true. Literal<Boolean>
