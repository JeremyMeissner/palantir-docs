---
source_url: "https://www.palantir.com/docs/foundry/foundryts/functions-first-point/"
parquet_url: "/foundry/foundryts/functions-first-point/"
title: "foundryts.functions.first_point"
fetched_at: "2026-05-12T19:34:36.037Z"
---
foundryts.functions.first_point. foundryts.functions.first_point(). Returns a function that extracts the earliest point for a single time series. The returned point is the first occuring point within the range of a given time series. Returns an empty summary when the series is empty. Returns: A function that accepts a single time series and returns the first point in the provided series. The dataframe contains a single row with the first point. Return type: (FunctionNode) -> SummarizerNode. Dataframe schema. Column nameTypeDescription timestamp. pandas.Timestamp. Timestamp of the point. value. Union[float, str] Value of the point. See Also. time_extent(), last_point(). Examples. 1 2 3 4 5 6 7 8 9 10 11 12 >>> series = F.points( ... (1, 0.0), ... (101, 10.2), ... (200, 11.3), ... (123450, 11.8), ... ) >>> series.to_pandas() timestamp value 0 1970-01-01 00:00:00.000000001 0.0 1 1970-01-01 00:00:00.000000101 10.2 2 1970-01-01 00:00:00.000000200 11.3 3 1970-01-01 00:00:00.000123450 11.8. 1 2 3 4 >>> fp = F.first_point()(series) >>> fp.to_pandas() timestamp value 0 1970-01-01 00:00:00.000000001 0.0.
