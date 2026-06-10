---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/windowedProjectV1/"
title: "Project over window"
---
# Project over window

Supported in: Batch, Faster, Streaming. Performs the specified aggregations on the data within the window. Emits one row each time a new row is received. Transform categories: Aggregate. Declared arguments. Dataset: Dataset to perform aggregations on. Table. Expressions: List of expressions to evaluate over the window. List<Expression<AnyType>> Window: Window to group data by. Window.
