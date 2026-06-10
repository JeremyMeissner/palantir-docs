---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/extractOffsetFromLegacyOffsetDateTimeV1/"
title: "Extract offset from legacy OffsetDateTime"
---
# Extract offset from legacy OffsetDateTime

Supported in: Batch. Extracts the offset from a legacy OffsetDateTime column. This is the offset in seconds of the origin timezone of the timestamp from UTC timezone. Expression categories: Datetime. Declared arguments. Expression: The legacy OffsetDateTime column. Expression<Struct<timestamp, offset>> Output type: Integer. Examples. Example 1: Base case. Argument values: Expression: col_a. col_aOutput { offset: 0, timestamp: 2024-09-09T09:00:00.001Z, } 0. { offset: 19800, timestamp: 2024-09-09T09:00:00.001Z, } 19800. { offset: -3600, timestamp: 2024-09-09T09:00:00.001Z, } -3600. Example 2: Null case. Argument values: Expression: col_a. col_aOutput null. null. { offset: 19800, timestamp: null, } 19800. { offset: null, timestamp: 2024-09-09T09:00:00.001Z, } 0.
