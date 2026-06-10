---
source_url: "https://www.palantir.com/docs/foundry/carbon/"
title: "Documentation | Carbon > Overview"
---
# Carbon

The Carbon application enables the configuration of custom platform experiences, known as [workspaces](/docs/foundry/carbon/workspaces-overview/), for specific user groups. Carbon can provide a focused experience for less technical users that need to carry out critical operational workflows.

For example, a Carbon workspace for aircraft parts maintenance might consist of:

* A [Workshop](/docs/foundry/workshop/overview/) module containing a dynamically updated list of parts requiring maintenance,
* A set of [Foundry Actions](/docs/foundry/action-types/overview/) for triaging each part,
* A [module](/docs/foundry/carbon/modules-overview/) that can be used to investigate each part's maintenance issue,
* A [Quiver](/docs/foundry/quiver/overview/) analysis showing maintenance trends over time.

Administrators can create multiple Carbon workspaces tailored to specific user profiles and governed by robust [permissions](/docs/foundry/carbon/permissions-configure/). In each workspace, administrators can highlight relevant workflows and applications, selectively hide the complexity of the overall platform, and restrict navigation outside of the Carbon workspace if necessary.

Carbon workspaces have a customized landing page along with a configured set of modules. When accessing Foundry through a Carbon workspace, a user will see only the subset of applications and resources needed for a specific workflow.

This documentation covers the basics of how to create, configure, and manage Carbon workspaces, as well as examples of several different workspace configurations.
## Access Carbon

Within Foundry, access Carbon by navigating to the Applications Portal and choosing **Carbon workspaces**. If you have already created a Carbon workspace and [promoted it as an available application](/docs/foundry/app-building/curating-apps/#promoted-apps-in-applications-portal), you can search for the workspace name under the **Promoted apps** section of the Application Portal.
