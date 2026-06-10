---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/frontendLazOuterCachingJoinV1/"
title: "Lazarus outer caching join"
---
# Lazarus outer caching join

Supported in: Streaming. Rows from the left & right inputs which meet all of the match conditions and are within the caching window, along with unmatched rows from both inputs. Transform categories: Join. Declared arguments. Default cache time unit: Default unit for amount of time data will be cached for before eviction for both the lhs and rhs cache. Enum<Days, Hours, Milliseconds, Minutes, Seconds, Weeks> Default cache time value: Default value for the amount of time data will be cached for before eviction for both the lhs and rhs cache. Literal<Long> Join key: A list of columns from left and right input to join on. List<Tuple<Column<AnyType>, Column<AnyType>>> Left columns to keep: Left columns to keep. List<Column<AnyType>> Left dataset: Left dataset to use in join. Table. Right columns to keep: Right columns to keep. List<Column<AnyType>> Right dataset: Right dataset to use in join. Table. optional Prefix for columns from right: Prefix for columns from right. Literal<String> optional Rhs cache time override: Value and unit of time that data from the rhs dataset will be cached for before eviction. Tuple<Literal<Long>, Enum<Days, Hours, Milliseconds, Minutes, Seconds, Weeks>>
