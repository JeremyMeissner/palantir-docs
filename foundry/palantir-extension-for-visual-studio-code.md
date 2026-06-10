---
source_url: "https://www.palantir.com/docs/foundry/palantir-extension-for-visual-studio-code/"
title: "Documentation | Palantir extension for Visual Studio Code > Overview"
---
# Palantir extension for Visual Studio Code

:::callout{theme="neutral"}
VS Code workspaces and the Palantir extension for Visual Studio Code are not affiliated with or endorsed by Microsoft.
:::

The Palantir extension for Visual Studio Code aims to integrate many features you see in [Code Repositories](/docs/foundry/code-repositories/overview/) with VS Code. The extension's features are currently focused on Python transforms.

## Access the extension

The Palantir extension for VS Code can be used either as part of a VS Code workspace in the Palantir platform, or as a downloadable extension for your local version of VS Code.

For guidance on choosing between these options, review our documentation on [choosing between local development and VS Code workspaces](/docs/foundry/vs-code/local-vs-workspace-guide/).

### From a VS Code workspace

The Palantir extension is available by default in VS Code workspaces. Review the [VS Code workspaces documentation](/docs/foundry/vs-code/overview/) to learn more.
### Locally

The Palantir extension can also be used in local development, and is the endorsed method for local development for Python transforms.

:::callout{theme="warning"}
You may not have the required permissions to work with the extension locally even if it is available on your enrollment. A platform administrator is required to enable local extension use, and they can grant user access through [Control Panel settings](/docs/foundry/code-repositories/configure-repositories-in-control-panel/). <br><br>
In order to preview locally, users must have the above Control Panel settings enabled and have `downloader` permissions on the preview inputs, which are `s3-proxy:datasets-read` and `api:datasets-read`. These are privileged operations that allow users to download entire datasets locally, and should be granted with care. In cases where users cannot be granted this permission, the VS Code developer experience is still available through [Code Workspaces](/docs/foundry/vs-code/overview/), which guarantee strict data control.
:::

#### 1. Download the Palantir extension

1. Navigate to VS Code Workspaces, then select the settings icon next to the **VS Code** button in the upper right corner of your screen.
2. Choose **Local VS Code** from the dropdown menu to change the default button language.
3. Select the updated **Local VS Code** button and follow the instructions in the pop-up window to download the extension.

Note: You only need to download the extension if you have never installed it before.
:::callout{theme="warning"}
The Palantir extension for Visual Studio code is not yet available in the Visual Studio Code Marketplace. You can only download the extension from the Palantir platform at this time.
:::

#### 2. Install the extension

Install the extension by performing one of the following steps:

* Drag and drop the VSIX file into the VS Code's **Extensions** sidebar, or
* Use the command `Extensions: Install from VSIX...`

#### 3. Open a Palantir code repository

Once the Palantir extension is installed, you should see the Palantir logo on the VS Code sidebar. From the sidebar, you can do one of the following:

* Open a Palantir repository that you already cloned, or
* Select **Clone a repository** to clone a new Palantir repository. To do this, open a Palantir repository and copy the git remote URL link.

[Review other features of the Palantir extension for Visual Studio Code](/docs/foundry/palantir-extension-for-visual-studio-code/extension-features/).
