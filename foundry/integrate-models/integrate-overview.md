---
source_url: "https://www.palantir.com/docs/foundry/integrate-models/integrate-overview/"
title: "Models"
---
# Models

Palantir provides a common interface to integrate models from a range of different sources. Models can be integrated from: Models trained in Palantir. Model files trained outside of Palantir and uploaded as an unstructured dataset. Models containerized outside of Palantir and pushed into the Foundry Docker registry. Models trained and hosted outside of Palantir. All models can be productionized and connected to operational applications through the Modeling Objectives application. Model adapters. Models in Palantir comprise of two components: Model artifacts: The model files, parameters, weights, container, or credentials where a trained model is saved. Model adapter: The logic and the environment dependencies that describes how Foundry should interact with the model artifacts to load, initialize, and perform inference with the model.
