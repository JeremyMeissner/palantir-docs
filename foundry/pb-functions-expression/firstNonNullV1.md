---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/firstNonNullV1/"
parquet_url: "/foundry/pb-functions-expression/firstNonNullV1/"
title: "First non null value (coalesce)"
fetched_at: "2026-05-12T19:34:36.746Z"
---
First non null value (coalesce). Supported in: Batch, Faster, Streaming. Picks first non null value of the inputs. Known as coalesce in sql. Expression categories: Data preparation. Declared arguments. Expressions: The first non null values of these expressions will be returned. List<Expression<T>> optional Treat empty strings as null: Treat all empty strings as null values. Literal<Boolean> Type variable bounds: T accepts AnyType. Output type: T. Examples. Example 1: Base case. Argument values: Expressions: [tail_number, airline] Treat empty strings as null: null. tail_numberairlineOutput XB-123. null. XB-123. null. MT. MT. Example 2: Base case. Argument values: Expressions: [tail_number, airline] Treat empty strings as null: true. tail_numberairlineOutput XB-123. null. XB-123. empty string. MT. MT. Example 3: Null case. Argument values: Expressions: [tail_number, airline] Treat empty strings as null: null. tail_numberairlineOutput null. null. null.
