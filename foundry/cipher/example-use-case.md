---
source_url: "https://www.palantir.com/docs/foundry/cipher/example-use-case/"
parquet_url: "/foundry/cipher/example-use-case/"
title: "Example Cipher use case"
fetched_at: "2026-05-12T19:34:36.933Z"
---
Example Cipher use case. One common use case for Cipher is to encrypt sensitive data by default, but allow operational users with legitimate purposes to selectively decrypt specific fields when they need it with an audit trail of actions. In the example diagram below, sensitive data lands in a Foundry dataset with a security Marking applied. The steps outline how to use Cipher to obfuscate data before sharing, and enabling only targeted decryptions for operational users. Steps to reproduce. Create a Cipher Channel in your landing Project. Issue an Admin License and grant access to it to a relevant admin user. Obfuscate sensitive columns via Transforms and unmark the minimized dataset. Reference the minimized dataset in the Project to which operational users have access. Issue a decrypt Operational User License and move it to the Project for operational users. Set up your Ontology and enable rendering of encrypted values.
