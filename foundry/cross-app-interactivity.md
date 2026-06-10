---
source_url: "https://www.palantir.com/docs/foundry/cross-app-interactivity/"
title: "Documentation | Cross-application interactivity > Overview"
---
# Cross-application interactivity

Cross-application interactivity is the ability to share data across distinct applications on the Palantir platform. Data in the platform can be shared through specific interaction points, such as through drag-and-drop actions, or by pairing applications so they share state in real time. Applications that implement cross-application interactivity create an ecosystem in which users can seamlessly build workflows that span multiple applications across and between Gotham and Foundry. This ecosystem enables users to connect applications in novel ways, since each interaction point in an application creates a potential connection to every other application with an interaction point.

As an example, [drag-and-drop](/docs/foundry/cross-app-interactivity/drag-and-drop-overview/) functionality can enable users to drag data from Gaia into a [Workshop](/docs/foundry/workshop/overview/) application, while ensuring data compatibility through data [enrichment](/docs/foundry/cross-app-interactivity/enrichment-reference/). Additionally, users can configure Workshop's [App Pairing](/docs/foundry/workshop/widgets-app-pairing/) widget to connect supported Palantir platform applications (such as Gotham's Gaia and Graph) to their Workshop modules, allowing [commands](/docs/foundry/cross-app-interactivity/commands-overview/) to automatically target the paired platform application on execution.
Cross-application interactivity also acts as a plug-in point for third-party developers to extend existing functionality by sharing context between applications. As workflows change and business logic evolves, cross-application interactivity unlocks new and diverse ways to generate value with the Palantir platform.

## Support

Currently, all Gotham applications and many Foundry applications implement some form of cross-application interactivity. Applications built in [Workshop](/docs/foundry/workshop/overview/) and [Slate](/docs/foundry/slate/overview/), or with the assistance of [OSDK](/docs/foundry/ontology-sdk/overview/), can also implement cross-application interactivity.

## Common interactions

When coupled with drag-and-drop functionality, App Pairing and Commands enable users to perform the following:

* Execute a workflow that spans multiple applications simultaneously.
* Move data between applications within a single workflow.
* Execute a workflow in one application that requires the use of capabilities native in a second or third.
* Connect their application to other ontology-backed applications.
* Configure [AIP Chatbots](/docs/foundry/chatbot-studio/overview/) (formerly known as AIP Agents) which can execute operations in an application on behalf of a user.

The sections below outline common interactions supported by the functionality of cross-application interactivity.

### Transition workflows and data between applications

When a user completes a task, often the next step is to transition their workflow to another application to continue its execution. Use commands within the [Button Group](/docs/foundry/cross-app-interactivity/commands-overview/#use-the-button-group-widget-to-configure-a-command) or [App Pairing](/docs/foundry/cross-app-interactivity/commands-overview/#use-the-app-pairing-widget-to-configure-a-command) widgets to pass data between applications.
Users can drag and drop data, such an object or object set, between applications when their workflow revolves around entity identification and triage.
### Sync selection state across applications

Configure the App Pairing widget or set commands to sync selection state when completing tasks that use multiple applications simultaneously. This enables users to view the same data using two complementary views and transition between the applications without losing state.
Additionally, users can embed one application within another to leverage existing views they integrate using the App Pairing widget.

:::callout{theme="neutral"}
Users should embed only the applications they need into an existing application, as embedding multiple may impact performance.
:::

### Provide context to AIP

The App Pairing and Commands widgets can read application state from the current viewport or selection and provide that context to [AIP Logic](/docs/foundry/logic/overview/).
Additionally, users can configure chatbots in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/) that leverage commands as [tools](/docs/foundry/chatbot-studio/tools/#types-of-tools) to read from and write to any application that can interoperate with commands, such as Gaia.
### Connect to the broader ecosystem

Users can [create drag-and-drop integration points](/docs/foundry/cross-app-interactivity/tutorial/#create-drag-and-drop-integration-points) to harness the power of their ontology and connect their application to others with similar integrations now and in the future.
