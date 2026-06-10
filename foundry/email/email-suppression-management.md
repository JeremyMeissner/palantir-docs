---
source_url: "https://www.palantir.com/docs/foundry/email/email-suppression-management/"
parquet_url: "/foundry/email/email-suppression-management/"
title: "Email suppression management"
fetched_at: "2026-05-12T19:34:35.940Z"
---
Email suppression management. Suppression management improves the explainability of email sending failures. As described in the overview, email sending may fail for a variety of reasons. When these failures are repeated (for example, when the recipient's email server is unavailable), either the platform or the underlying email provider could create a "suppression", a mechanism by which the platform stops sending email to a user until the suppression expires or is manually deleted. Suppressions caused by a BOUNCE will be automatically deleted after 14 days, while suppressions caused by user COMPLAINT will require manual intervention to delete. We do not recommend deleting suppressions caused by a COMPLAINT without explicit consent from the recipient. Doing so could affect your email sending reputation and negatively impact your email deliverability.
