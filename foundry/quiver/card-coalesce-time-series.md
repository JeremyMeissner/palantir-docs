---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-coalesce-time-series/"
title: "Coalesce time series"
---
# Coalesce time series

The coalesce time series card returns the first time series that is not null or errored, or null if all input series are null. This card is useful for casting potential null series to a defined series. To do this, use a variable input to select a card or column value that is potentially null as the first array value. For the second array value, choose a non-null "fallback" time series for cases when the first value is null. Input type. Time series array. Output type. Time series. Examples. Usage information. FunctionalityAvailability Standard Quiver card. Supported. Transform table transform. Supported. See also. Coalesce.
