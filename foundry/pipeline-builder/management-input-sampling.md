---
source_url: "https://www.palantir.com/docs/foundry/pipeline-builder/management-input-sampling/"
parquet_url: "/foundry/pipeline-builder/management-input-sampling/"
title: "Add an input sampling strategy"
fetched_at: "2026-05-12T19:34:37.104Z"
---
Add an input sampling strategy. If your input datasets are large, you can speed up preview times by adding a sampling strategy to those inputs. Right-click the input node that you would like to sample, then select Sampling strategies in the dropdown menu. From the sampling strategies dialog, select the desired input dataset. Choose the Percentage strategy, and enter a number between 1 and 100 to downsample your input. Close the dialog. A blue badge should now appear on the top right of your input node, indicating that a sampling strategy has been applied. The preview panel of any nodes downstream of the input will also indicate that sampling was applied.
