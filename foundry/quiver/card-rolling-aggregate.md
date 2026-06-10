---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-rolling-aggregate/"
title: "Rolling aggregate"
---
# Rolling aggregate

Rolling aggregates are typically used to “smooth” a series and show an averaged version of it. For each point in your series, a Rolling aggregate will calculate a new point based on your window function and aggregate method. As an example, if you choose a window size of one week and method average, each point will be calculated by finding the average value over the previous week. If you choose a window size of three days and method sum, then each point will be the sum of the previous three days. Windows are calculated by previous values up to and including that point. Input type. Time series. Output type. Time series. Example. Usage information. FunctionalityAvailability Standard Quiver card. Supported. Transform table transform. Supported.
