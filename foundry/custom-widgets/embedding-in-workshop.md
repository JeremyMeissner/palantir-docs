---
source_url: "https://www.palantir.com/docs/foundry/custom-widgets/embedding-in-workshop/"
parquet_url: "/foundry/custom-widgets/embedding-in-workshop/"
title: "Embedding a widget in Workshop"
fetched_at: "2026-05-12T19:34:36.052Z"
---
Embedding a widget in Workshop. To embed a widget in Workshop, start by adding a custom widget component to your Workshop: In the new Widget setup tab, find Select to select the widget set and version to use. Configure parameters and events. You can bind the parameters your widget uses to Workshop variables to allow passing data in and out of the Workshop state. For information on the different parameter types available, see parameters and events. You can use events to allow widgets to update the parameter values. You can also bind these events to Workshop events such that when a widget fires an event, it will also trigger a Workshop event. Widget parameters and events can be bound to Workshop variables and events in the Widget setup panel: Limitations. Custom widgets currently reload every time they are removed from the page and later displayed again. To prevent the widget from resetting in this case, consider storing custom widget data in Workshop variables that are passed to the widget.
