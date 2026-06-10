---
source_url: "https://www.palantir.com/docs/foundry/custom-widgets/auto-sizing/"
parquet_url: "/foundry/custom-widgets/auto-sizing/"
title: "Auto sizing"
fetched_at: "2026-05-12T19:34:36.044Z"
---
Auto sizing. Custom widgets can be used in two types of layouts: To fill the provided container space given by the parent application, for example in Workshop "absolute" and "flex" layouts. To control the container size based on content size, for example in Workshop "auto" layouts. To achieve option one, custom widget styles can apply height: 100% and/or width: 100% as is appropriate to the document HTML and body elements. This should make child content responsive to the available space. To achieve option two, the height and/or width of the document body element will be used for auto sizing in the parent application. Custom widget styles should not apply height: 100% or width: 100% to the document HTML and body elements. Instead, custom widget styles should ensure that the size of the document body element responsively grows or shrinks with respect to the size of its child content. A minimum version of @osdk/widget.client-react ↗ 3.3.0 is required for this functionality.
