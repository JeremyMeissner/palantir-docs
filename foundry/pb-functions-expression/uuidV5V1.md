---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/uuidV5V1/"
title: "UUID V5"
---
# UUID V5

Supported in: Batch, Streaming. Generates a deterministic UUID v5 from a namespace UUID and a name string using SHA-1 hashing (RFC 4122). The same namespace and name will always produce the same UUID. Returns null if the namespace is not a valid UUID. Expression categories: String. Declared arguments. Name: The name string to hash with the namespace to produce a deterministic UUID. Expression<String> Namespace UUID: A valid UUID string to use as the namespace. Expression<String> Output type: String. Examples. Example 1: Base case. Description: Generate a deterministic UUID v5 from a namespace UUID and name string. Argument values: Name: name. Namespace UUID: namespace. namespacenameOutput 6ba7b810-9dad-11d1-80b4-00c04fd430c8. hello. 9342d47a-1bab-5709-9869-c840b2eac501. 6ba7b811-9dad-11d1-80b4-00c04fd430c8. https://example.com. 4fd35a71-71ef-5a55-a9d9-aa75c889a6d0. Example 2: Null case. Argument values: Name: name. Namespace UUID: namespace. namespacenameOutput null. hello. null. 6ba7b810-9dad-11d1-80b4-00c04fd430c8. null. null. null. null. null. Example 3: Edge case. Argument values: Name: name. Namespace UUID: namespace. namespacenameOutput not-a-uuid. hello. null.
