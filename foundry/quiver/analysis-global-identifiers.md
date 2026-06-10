---
source_url: "https://www.palantir.com/docs/foundry/quiver/analysis-global-identifiers/"
parquet_url: "/foundry/quiver/analysis-global-identifiers/"
title: "Global identifiers (IDs)"
fetched_at: "2026-05-12T19:34:37.911Z"
---
Global identifiers (IDs). Unique Quiver global identifiers (IDs) in the form of $A are automatically assigned to all Quiver cards when added to an analysis. Identify global IDs. Global ID values can be seen in various places across Quiver: Next to each card and plot in the Analysis contents panel. Next to each parameter in the Parameters panel. For each card in the card's header and the editor panel. For each parameterized input value in the editor panel. In the legend of a time series chart for each time series plot. In the axis of a time series chart for each shared axis. Use global IDs. Global IDs are used in formulas and Vega plot configurations to reference data sources, such as time series plots, transform tables, charts, arrays, or scalar values. For example, you can reference a transform table with its global ID (such as $B) in the data section of a Vega plot. To reference specific columns in a transform table, use the syntax $A.column_name. Similarly, you can reference scalar values using the global ID of a numeric metric card (like $C).
