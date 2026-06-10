---
source_url: "https://www.palantir.com/docs/gotham/platform-security-third-party/"
title: "Documentation | Third-party applications > Overview"
---
# Overview

Palantir's platform security controls ensure that integration and interoperability with third-party applications can be centrally managed while respecting established security measures. Third-party application authorization supports the [OAuth 2.0 framework](/docs/gotham/platform-security-third-party/writing-oauth2-clients/).

Third-party application permissions should be managed by Gotham administrators to ensure the security of the platform. The third-party application interface in **Platform Settings** enables Gotham administrators to see which applications have been registered as well as which applications have been enabled for access. From the third-party application interface, administrators can [register new applications](/docs/gotham/platform-security-third-party/register-3pa/), [manage existing applications](/docs/gotham/platform-security-third-party/manage-3pa/), and [disable or revoke application registrations](/docs/gotham/platform-security-third-party/danger-zone-actions/#delete-an-application-registration).

## Accessing the third-party applications user interface

For users with the appropriate permissions, the third-party application management interface can be reached by navigating to the **Settings** page (`/workspace/settings`) via the Account icon (your initials) in the lower-left-hand corner of the navigation bar, then selecting the **Third-party applications** tab.
To access the third-party application management interface, you must have “Manage OAuth2 Clients” access for your primary Organization, as seen on the Organizations tab of the Settings page (`/workspace/settings/organizations`). Contact your Palantir representative to request access. Without this permission, the third-party applications tab will not appear on the Settings page.
