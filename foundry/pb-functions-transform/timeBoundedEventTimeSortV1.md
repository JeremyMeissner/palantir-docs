---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/timeBoundedEventTimeSortV1/"
title: "Time bounded event time sort"
---
# Time bounded event time sort

Supported in: Streaming. Emits rows by key in ascending event time order, allowing for late arriving records up until at least the allowed lateness. Records arriving after the allowed lateness plus some small buffer interval will be dropped. Transform categories: Other. Declared arguments. Allowed lateness time unit: Unit for amount of time to wait for late arriving records to be sorted. Enum<Days, Hours, Milliseconds, Minutes, Seconds, Weeks> Allowed lateness time value: Value for amount of time to wait for late arriving records to be sorted. Literal<Long> Dataset: Dataset to sort rows. Table. optional Key by columns: Columns on which to partition the input by key. Each sort will be computed separately for each distinct key value. Set<Column<AnyType>>
