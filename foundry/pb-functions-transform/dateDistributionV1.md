---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/dateDistributionV1/"
title: "Date distribution"
---
# Date distribution

Supported in: Batch. Computes the distribution of dates/timestamps in a specified column. Transform categories: Datetime. Declared arguments. Column: Column to compute distribution for. Column<Date | Timestamp> Dataset: Dataset to apply distribution to. Table. End time: End time for distribution. Any time after will be ignored. Literal<Date | Timestamp> Start time: Start time for distribution. Any time before will be ignored. Literal<Date | Timestamp> Time bucket: The time unit to use for buckets. Enum<Day, Hour, Minute, Month, Second, Week, Year>
