---
source_url: "https://www.palantir.com/docs/foundry/manage-models/archive-model/"
title: "Archive models in an objective"
---
# Archive models in an objective

As a modeling objective matures and accumulates many model submissions, it can be useful to archive old or rejected model submissions to make the objective easier to work with and understand. Archiving a model submission has several effects: Removes the ability to create a release from that model. Moves the model submission into the Archive table, accessible by clicking on the View archive link in the top right section of the Models view. Foundry provides model archiving instead of hard deletion because objectives can act as an important system of record for models that have been previously deployed and used for operational decision-making. To archive a model submission, navigate to the model submission's individual page, click on the Actions button in the top right corner, and select Archive. Models that have been marked as a release are unable to be archived. Clean up. After archiving a model submission, don't forget to adjust or remove the build schedule of any configured metric management pipelines.
