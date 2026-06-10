---
source_url: "https://www.palantir.com/docs/foundry/model-integration/functions-on-models/"
title: "Functions on models"
---
# Functions on models

You can deploy models as functions to enable live usage of models in end-user applications like Workshop, Slate, Actions, and more. Model functions can also be used in other functions to write custom business logic involving the model in code. Publish a function for your model. Functions can be published for models with a live deployment configured, or for Modeling Objectives live deployments. Learn more about how to configure and manage model functions. Call a model function in code. Below is a simplified example of a function that calls a live deployment that takes an input Double[] and returns a Double[] output called output_df in the model API: 1 2 3 4 5 6 7 8 import { Function, Double } from "@foundry/functions-api"; import { ModelDeployment } from "@foundry/models-api/deployments"; @Function() public async predictValues(inputs: Double[]): Promise<Double[]> { const modelOutput = await ModelDeployment(inputs); return modelOutput.output_df; } Learn more about how to use model functions in other functions.
