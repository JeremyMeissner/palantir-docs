---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-linked-series-aggregation/"
title: "Linked series aggregation"
---
# Linked series aggregation

Generates a new time series by performing a linear aggregation on time series data from linked objects. Start from a single object, search around to linked objects, and aggregate series of a given type on these objects. Event options. Event options can be configured to search for event objects and align the time series relative to the event start time. Starting from the same object, search around to event objects, define the start and end time properties, and provide a common key between the time series and event objects. The resulting time series objects and event objects will be inner joined on the common key, and the time series will be filtered to the event start and end times and aligned relative to the event start time before being aggregated. The resulting time series will be in relative time. Input type. Object. Output type. Time series. Example. Without event options: With event options: Usage information. FunctionalityAvailability Standard Quiver card. Supported. Transform table transform. Unsupported. See also. Linear aggregation. Reference profiles in derived series.
