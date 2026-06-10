---
source_url: "https://www.palantir.com/docs/foundry/announcements/"
title: "Documentation | Announcements > June 2026"
---
# Announcements

**REMINDER:** Sign up for the Foundry Newsletter to receive a summary of new products, features, and improvements across the platform directly to your inbox. For more information on how to subscribe, see the [Foundry Newsletter and Product Feedback channels announcement](/docs/foundry/announcements/2023-11/#foundry-newsletter-and-product-feedback-channels-available-for-sign-up-now-ga).

Share your thoughts about these announcements in our [Developer Community Forum ↗](https://community.palantir.com/c/announcements/6).

***

## Pipeline Builder: Media sets now supported in Faster pipelines

Date published: 2026-06-09

Faster pipelines now accept media sets as inputs. You can process PDFs, images, and audio files in a Faster pipeline and convert them into structured data for downstream extraction, classification, analysis, or review.

For more information, see the [media sets](/docs/foundry/data-integration/media-sets/) documentation.
*Use media sets in Faster pipelines to transform media file inputs.*

### Supported inputs

With media set support in Faster pipelines, you can now build pipeline workflows that take PDFs, images, and audio files as direct inputs. Supported use cases include:

* **PDF and image OCR:** Transform PDF and image files into structured data for further extraction or classification.
* **PDF text extraction:** Extract key text strings from PDFs to classify, summarize, or validate data.
* **Audio transcription:** Convert spoken conversations from audio files into structured text data.

### Add a media set to a Faster pipeline

* Create a new pipeline and select **Faster**.
* Add media to your pipeline by selecting existing Foundry media, uploading new media to Foundry, or uploading new media directly to the Faster pipeline from your computer.
* Select the **Write mode**. You can choose between **Transactionless** (recommended) and **Transactional**.

Ensure your media files are uploaded to a new media set.
*Select the upload to a new media set option when uploading media files*

### Share your feedback

As we continue to add features to Pipeline Builder, we want to hear about your experiences and welcome your feedback. Share your thoughts with Palantir Support channels or our [Developer Community ↗](https://community.palantir.com/) using the [`pipeline-builder` tag ↗](https://community.palantir.com/tag/pipeline-builder).

***

## Python transform editing in Code Repositories will soon be legacy

Date published: 2026-06-04

Starting the week of June 22, editing Python transforms in Code Repositories will move to the [legacy phase of development](/docs/foundry/platform-overview/development-life-cycle/#legacy). [VS Code workspaces](/docs/foundry/vs-code/overview/) are the recommended environment for editing Python transforms, offering AI-powered coding assistance, full dataset preview, an optimized language server, and an integrated terminal.

The Code Repositories editor will remain supported and available, with future feature development focused on VS Code workspaces. Code Repositories remains the recommended editor for other repository types, including Java and SQL transforms.

If VS Code workspaces are unavailable on your enrollment, Code Repositories remains the recommended way to author Python transforms.

### Getting started

To get started with VS Code workspaces for Python transforms, we recommend reviewing the following documentation:

* [VS Code workspaces: Overview](/docs/foundry/vs-code/overview/)
* [Reference: VS Code workspaces vs. Code Repositories](/docs/foundry/vs-code/overview/#reference-vs-code-workspaces-vs-code-repositories)
* [Benefits of VS Code workspaces](/docs/foundry/vs-code/benefits/)

***

## Pipeline Builder: GeoExpressions now supported in Faster pipelines

Date published: 2026-06-04

Faster pipelines in Pipeline Builder now support more than 25 built-in GeoExpressions for cleaning, transforming, and visualizing geospatial data without needing to leave the platform or write custom code. Supported operations include geometry intersections, GeoJSON parsing, GeoPoint conversions, and more.

[To learn more, see GeoExpressions in Pipeline Builder.](/docs/foundry/pipeline-builder/transforms-geospatial/)

The team is actively adding more GeoExpressions which will automatically become available for your Faster pipelines.

### Use GeoExpressions in Faster pipeline

* Create a new Transform board in the graph view.
* In the Transform board menu, search for the expression or select **Geospatial** from the left panel.
* Select the GeoExpression to apply to your data.
*The Geospatial option from the Transform board menu.*

### Use Geo Preview in a Faster pipeline

* After transforming your data, open the preview pane.
* Select the cells you want to view on a map. The cells must be from columns with a supported geospatial logical type.
* Right-click the selected cells, then choose **Open Geo Preview**. The selected cells appear plotted on a map in a new tab.
*Geo Preview in Pipeline Builder.*

### Compatibility and downstream behavior

* Builder geometry column types in Faster pipelines are compatible with the Ontology `geoshape` type. To learn more, see [using geospatial data with the Ontology](/docs/foundry/pipeline-builder/transforms-geospatial/#using-geospatial-data-with-the-ontology).
* Geospatial type data is persisted on output datasets from Faster Pipelines. Downstream Builder pipelines created from these datasets will preserve logical and geospatial types.
* GeoPoint and geometry columns can be mapped to a geotemporal series sync output to render points and geometries in downstream applications. To learn more, see [using geospatial data with the Ontology](/docs/foundry/pipeline-builder/transforms-geospatial/#using-geospatial-data-with-the-ontology).

### Commonly used GeoExpressions include:

* Convert MGRS to GeoPoint
* Is valid GeoJSON
* Parse well known text as geometry
* Parse GeoJSON from a non-WGS 84 coordinate system
* Simplify geometry
* Geometries have intersection
* Geometry intersection
* Get the convex hull of a geometry
* Convert linestring to polygon
* Geometry array (unary) union

### We want to hear from you

Send feedback through Palantir Support or the [Developer Community](https://community.palantir.com/) using the [pipeline-builder tag](https://community.palantir.com/tag/pipeline-builder).

***

## Claude Opus 4.8 now available from Anthropic, AWS Bedrock, and Google Vertex

Date published: 2026-06-02

Claude Opus 4.8 is now available on non-georestricted enrollments from Anthropic, AWS Bedrock, and Google Vertex. For US, EU, and non-georestricted enrollments, the model is available from AWS Bedrock and Google Vertex. For JP georestricted enrollments, the model is available from AWS Bedrock.

### Model overview

Claude Opus 4.8 adds improvements in coding, long-running autonomous agents, and reasoning on complex enterprise problems. For more information, review [Anthropic's model documentation ↗](https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-8).

* **Context window:** 1,000,000 tokens
* **Modalities:** Text, image
* **Capabilities:** Extended thinking, function calling

### Getting started

To use this model:

* [Confirm that your enrollment administrator has enabled the relevant model family.](/docs/foundry/aip/enable-aip-features/#enable-llms)
* Review [token costs and pricing](/docs/foundry/aip/aip-compute-usage/#tokens-in-aip).
* See the complete [list of all available models in AIP](/docs/foundry/aip/supported-llms/).

### Your feedback matters

We want to hear about your experiences using language models in the Palantir platform and welcome your feedback. Share your thoughts with Palantir Support channels or on our [Developer Community ↗](https://community.palantir.com/) using the [language-model-service tag ↗](https://community.palantir.com/tag/language-model-service).

***

## Visualize Workshop modules with the new variable lineage graph

Date published: 2026-06-01

The **Variable lineage graph** is now generally available in Workshop. The graph replaces the previous variable dependency graph with a redesigned visualization for tracing how variables and widgets in a module depend on one another. Use it to debug recompute behavior, find which widgets read or write a given variable, and better understand complex relationships between your application's components.
*The* ***Variable lineage*** *graph mode shows variables, widgets, and their dependencies.*

### Expand the graph one node at a time

To open the new variable lineage panel, select the **Graph** button on the top right of the **Variables** panel in any Workshop module's edit mode.
*Use the* ***Graph*** *button, highlighted in red, to open the variable lineage panel.*

Each node on the graph represents a variable or widget. Nodes with dependencies now have chevron arrows on its top and bottom edges. Selecting an arrow expands a node's parents or children to trace a chain of dependencies through a large module. **Show all** and **Clear** actions in the header let you expand to the full application graph or remove all nodes. Undo and redo buttons in the header step backward and forward through expand, collapse, and selection actions.
*A detailed view of variable usage and computation time.*

### See where variables are referenced

Variable nodes are tagged with the pages and overlays where they are used. Toggle **Show pages and overlays** in the header to open a legend that lists each referenced page and overlay, alphabetized and split into separate sections. The legend only includes pages and overlays that appear on visible nodes so the list stays scoped to what you can actually see in the graph.

### Identify expensive variables

Toggle **Show computation time** in the header to display per-variable timing information. Variables that take longer to recompute may be candidates for restructuring: for example, splitting a complex function-backed variable into smaller pieces or changing the recompute behavior on upstream variables to avoid unnecessary work.

To read more about the variable lineage graph, see Workshop's [documentation on variables](/docs/foundry/workshop/concepts-variables/#variable-lineage-graph).

### Share your feedback

We want to hear about your experiences using Workshop in the Palantir platform and welcome your feedback. Share your thoughts through Palantir Support channels or on our [Developer Community ↗](https://community.palantir.com/) using the [`workshop` tag ↗](https://community.palantir.com/tag/workshop).
