---
source_url: "https://www.palantir.com/docs/foundry/automate/effects/"
title: "Effects"
---
# Effects

Effects define what happens when an automation is triggered. When a condition is met, the automation executes one or more effects to perform actions, apply logic, execute functions, or send notifications. Effect types. Automate supports the following types of effects: Action effects: Execute actions on objects, such as creating, modifying, or deleting object instances. Logic effects: Execute AIP Logic functions. Function effects: Execute a function when the automation condition is met. Notification effects: Send notifications to users or groups when the automation triggers. Fallback effects. Action, logic, and function effects can be configured with a fallback effect. Fallback effects execute when the primary effect fails, allowing you to handle errors gracefully by sending notifications, logging failures, or triggering alternative workflows. Effect settings. Configure how effects execute with effect settings, including: Concurrency: Run effects sequentially or in parallel. Object edits: Control how multiple edits are handled. Execution guarantees: Understand at-least-once execution semantics.
