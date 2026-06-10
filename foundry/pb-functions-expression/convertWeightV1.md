---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/convertWeightV1/"
title: "Convert between weight units"
---
# Convert between weight units

Supported in: Batch, Faster, Streaming. Expression categories: Numeric. Declared arguments. Amount of current unit: no description Expression<DefiniteNumeric> Current unit: The unit prior to conversion. Enum<Centigram, Decagram, Decigram, Grain, Gram, Hectogram, Kilogram, Long hundredweight, Megagram, Metric ton, and more ...> Target unit: The desired unit after conversion. Enum<Centigram, Decagram, Decigram, Grain, Gram, Hectogram, Kilogram, Long hundredweight, Megagram, Metric ton, and more ...> Output type: Double. Examples. Example 1: Base case. Argument values: Amount of current unit: kilograms. Current unit: kilogram. Target unit: gram. kilogramsOutput 5. 5000.0. Example 2: Base case. Argument values: Amount of current unit: kilograms. Current unit: kilogram. Target unit: gram. kilogramsOutput null. null.
