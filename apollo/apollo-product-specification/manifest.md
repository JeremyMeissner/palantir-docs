---
source_url: "https://www.palantir.com/docs/apollo/apollo-product-specification/manifest/"
title: "The Product Release Manifest"
---
# The Product Release Manifest

Every Apollo Product Release must include a manifest.yml file. This manifest includes immutable information about a Product, and must include the following top-level fields: product-type: the Product's type. product-group: The Product's maven coordinate ↗'s group ID. product-name: The Product's maven coordinate ↗'s artifact ID. product-version: The Product's maven coordinate ↗'s version. The product version must conform to the Apollo product version specification. Example. 1 2 3 4 product-type: service.v1 product-group: com.palantir.apollo product-name: apollo-catalog product-version: 1.2.3. Manifest Extensions. A Product Release manifest may also include extensions describing a Product's immutable characteristics. The Apollo Product Specification documents the manifest extensions supported by the Apollo Platform.
