---
source_url: "https://www.palantir.com/docs/foundry/vs-code/"
title: "Documentation | VS Code workspaces > Overview"
---
# VS Code workspaces

:::callout{theme="neutral"}
VS Code workspaces and the Palantir extension for Visual Studio Code are not affiliated with or endorsed by Microsoft.
:::

:::callout{theme="neutral"}
VS Code workspaces is available by default in all Organizations where Code Workspaces is enabled.
:::

VS Code workspaces bring the power of Microsoft's [VS Code ↗](https://github.com/microsoft/vscode) IDE directly into the Palantir platform. VS Code workspaces are development environments deployed on Palantir infrastructure that leverage [Code Workspaces](/docs/foundry/code-workspaces/overview/) to provide an integrated development environment (IDE) for writing production-ready code. Whether you are building Python transforms, developing OSDK React applications, or working on compute modules ([see a full list of supported workflows here](#supported-workflows)), VS Code workspaces provide a familiar, powerful environment with automatic environment setup and seamless integration with Foundry resources.

## Why use VS Code workspaces?

[Learn more about the benefits of VS Code workspaces.](/docs/foundry/vs-code/benefits/)

## Get started with VS Code workspaces

### Access a workspace

1. Open an existing or create a new [supported repository](#supported-workflows) in VS Code.
2. From Code Repositories, you can select **Open in VS Code** in the upper right corner (shown for supported repositories).
3. At the time of creating a new repository, selecting VS Code will automatically bring you into a VS Code workspace.
4. Your environment is ready, and you can start coding.
### Make VS Code your default editor

You can make VS Code your default code editor for all supported repository types by navigating to the **Settings** tab within any repository and selecting **Open repositories in a VS Code workspace by default**.
Note that some repositories will open in VS Code regardless of the default setting, since these repository types have been optimized for VS Code workspaces.

## Supported workflows

VS Code workspaces support the workflows described in the sections below.

### Python transforms

The Palantir extension automatically sets up your Python environment at startup and provides the following:

* [Preview integration](/docs/foundry/palantir-extension-for-visual-studio-code/transforms-preview/) with sample-less and code-defined filtering options
* [Debugging support](/docs/foundry/palantir-extension-for-visual-studio-code/debug-transforms/) with variable inspection
* [Build triggers](/docs/foundry/palantir-extension-for-visual-studio-code/transforms-build/) from inside your editor
* Resource paths displayed with resource identifiers for easy navigation
* Automatic code environment setup
* Code snippets for common patterns
[Learn more about Python transforms.](/docs/foundry/transforms-python/getting-started/)

### OSDK React applications

VS Code is integrated with [Developer Console](/docs/foundry/developer-console/overview/), allowing you to rapidly build React applications. You can create a VS Code workspace in the **Code repository** section of your Developer Console.
Key features include:

* Full Ontology integration with OSDK to interact with your unique Ontology resources
* Git repository configuration with OAuth pre-configured
* CI setup to deploy your website on every release
* Automatic node/npm environment setup
* Development server with live reload for instant feedback
[Learn more about OSDK React applications.](/docs/foundry/ontology-sdk-react-applications/overview/)

### Other supported workflows

* **[Compute modules](/docs/foundry/compute-modules/get-started/):** Build Python compute modules with run and debug capabilities.
* **[Python libraries](/docs/foundry/transforms-python/share-python-libraries/):** Develop and debug reusable Python libraries.

***

## Reference: VS Code workspaces vs. Code Repositories

VS Code and Code Repositories serve different primary purposes:

* **Code Repositories:** A Palantir-built IDE focused on all code-management needs, including editing, version control, change management, and continuous integration. This is the intended platform tool for pull request reviews and repository management.

* **VS Code:** A VS Code environment deployed on Palantir infrastructure and accessible from the Palantir platform. Provides the familiar VS Code editing experience with automatic environment setup and integration with Foundry resources through the [Palantir extension for Visual Studio Code](/docs/foundry/palantir-extension-for-visual-studio-code/overview/).

* **Palantir extension for Visual Studio Code (local):** An extension you install in your local VS Code application to integrate directly with Foundry. Provides preview, debug, and build capabilities for Python transforms while working on your local machine.

### Feature comparison

|                     Feature | Code Repositories                                                    | VS Code workspaces                   | Palantir extension for Visual Studio Code |
| --------------------------: | -------------------------------------------------------------------- | ------------------------------------ | ----------------------------------------- |
|              **Transforms** |                                                                      |                                      |                                           |
|    Python transform preview | Yes                                                                  | Yes                                  | Yes                                       |
|           Full data preview | Preview data sample, with the ability to pre-filter the input sample | Yes                                  | Yes                                       |
|            Debugger support | Yes                                                                  | Yes                                  | Yes                                       |
|             Java transforms | Yes                                                                  | No                                   | No                                        |
|                  Unit tests | Yes                                                                  | Yes                                  | Yes                                       |
| **OSDK React applications** |                                                                      |                                      |                                           |
|  Typescript Language Server | No                                                                   | Yes                                  | Yes                                       |
|    Live reload code changes | No                                                                   | Yes                                  | Yes                                       |
|  **Python compute modules** |                                                                      |                                      |                                           |
|  Run and debug Python files | No                                                                   | Yes                                  | Yes                                       |
|        **Python libraries** |                                                                      |                                      |                                           |
|  Run and debug Python files | No                                                                   | Yes                                  | Yes                                       |
|               **Workflows** |                                                                      |                                      |                                           |
|             SQL integration | Yes                                                                  | No                                   | No                                        |
| Typescript function preview | Yes                                                                  | No                                   | No                                        |
|                     **IDE** |                                                                      |                                      |                                           |
|              Shell terminal | No                                                                   | Yes (Remote host)                    | Yes                                       |
|    Keybinding customization | No                                                                   | Yes                                  | Yes                                       |
|    Public extension support | N/A                                                                  | No                                   | Yes, if allowed by your organization      |
|               AI Assistance | AIP Autocomplete                                                     | Yes, Continue extension              | No                                        |

## Choose your development environment

You have two options for using VS Code with Foundry. For a detailed comparison to help you decide which is right for you, review our documentation on [choosing between local development and VS Code workspaces](/docs/foundry/vs-code/local-vs-workspace-guide/).

The [Palantir extension for Visual Studio Code](/docs/foundry/palantir-extension-for-visual-studio-code/overview/) provides native integrations with the Palantir platform, including many features you see in [Code Repositories](/docs/foundry/code-repositories/overview/).

[Learn more about the features of the Palantir extension.](/docs/foundry/palantir-extension-for-visual-studio-code/extension-features/)

### Pricing

For VS Code workspace pricing information see [Code Workspaces compute usage](/docs/foundry/code-workspaces/compute-usage/).
