---
source_url: "https://www.palantir.com/docs/foundry/custom-docs/faq/"
parquet_url: "/foundry/custom-docs/faq/"
title: "FAQ"
fetched_at: "2026-05-12T19:34:37.250Z"
---
FAQ. What are the differences between standard Markdown and the syntax required for custom docs? The most important differences from standard Markdown in the in-platform custom documentation are: Page titles must be specified with the @ syntax (@name for overview.md or @title for non-overview pages), instead of an H1 header (#). Note that the actual filename and @title do not need to be the same. All pages must be specified in the ordering.md file to be published successfully. All pages must have a section annotation (for example, @concept or @howto). Does in-platform custom documentation support changelogs? No, changelogs for custom documentation are currently not supported. Does custom documentation support branching? You can work on branches in a documentation repository, but only the master branch is published to the in-platform custom documentation. Why does Markdown formatting not display in a callout? Since callouts are designated with HTML, Markdown formatting is not available between the <div> and </div> in the callout; for example, to bold text within a callout you should use the HTML syntax <strong>This is bold text.</strong> rather than the Markdown syntax **This is bold text.**.
