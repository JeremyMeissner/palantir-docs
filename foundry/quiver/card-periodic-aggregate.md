---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-periodic-aggregate/"
parquet_url: "/foundry/quiver/card-periodic-aggregate/"
title: "Periodic aggregate"
fetched_at: "2026-05-12T19:34:37.899Z"
---
Periodic aggregate. Periodic aggregates are similar to Rolling aggregates except that they downsample the data. If you have daily data and perform a Rolling aggregate using a window of one week with an average function, your chart will return a series with one point per day, with each point representing the previous week’s average. However, if you do a Periodic aggregate with a window of one week, your new series will have one point per week rather than one point per day. Input type. Time series. Output type. Time series. Examples. Usage information. FunctionalityAvailability Standard Quiver card. Supported. Transform table transform. Supported. See also. Rolling aggregate.
