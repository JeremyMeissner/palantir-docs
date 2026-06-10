---
source_url: "https://www.palantir.com/docs/foundry/quiver/cards-formulas/"
title: "Formulas"
---
# Formulas

Several types of Quiver cards allow you to type mathematical expressions into a formula box to transform data in your analysis. Inputs of formulas can be numbers, categorical charts, or time series. Quiver uses a custom mathematical expression language for formulas. Basic arithmetic operations are supported (multiplication, division, addition, subtraction, etc.), along with more complex mathematical expressions. You can refer to data in your analysis by using their global identifiers (e.g. $A). Quiver’s autocomplete will suggest built-in functions, along with matching inputs from your analysis based on their name. The following Quiver card types support formulas: Numeric formula. Numeric series formula. Time series formula. Categorical formula plot. Segment formula plot. Formulas can also be found in some transform table transformations, such as Boolean formulas, numeric formulas, or time series formulas. In the transform table, you can reference input columns in formulas using the @ symbol (e.g. @column > 0). Consult the formula syntax documentation for more details about supported expressions.
