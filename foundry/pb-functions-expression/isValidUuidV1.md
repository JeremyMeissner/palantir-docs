---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isValidUuidV1/"
parquet_url: "/foundry/pb-functions-expression/isValidUuidV1/"
title: "Is valid uuid"
fetched_at: "2026-05-12T19:34:36.643Z"
---
Is valid uuid. Supported in: Batch, Faster, Streaming. Returns true if the input is a valid uuid. Expression categories: Boolean. Declared arguments. Expression: String representing a uuid. Expression<String> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: uuid. uuidOutput 5c5622fe-e30e-4491-99b6-6213be506dec. true. 9daf08e9-d2e2-4172-86cc-9102c4c770b3. true. 9DAF08E9-D2E2-4172-86CC-9102C4C770B3. true. UUID with text before 9daf08e9-d2e2-4172-86cc-9102c4c770b3. false. a1-a1-a1-a1-a1. false. not a uuid. false. Example 2: Null case. Argument values: Expression: uuid. uuidOutput null. false.
