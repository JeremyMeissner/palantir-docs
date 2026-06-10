---
source_url: "https://www.palantir.com/docs/apollo/managing-labels/overview/"
title: "Overview"
---
# Overview

You can use labels to tag resources in Apollo with important details, such as the type of infrastructure of an Environment, the component of an Entity in your application, or to denote that a Product Release has been scanned. Labels are defined as key-value pairs and have the following components: Label ID: A unique identifier for the label. The label ID has an optional prefix and a label name, which are separated by the / character. For example, com.palantir.apollo/label-name and label-name are both valid label IDs. Label value: This field contains information that corresponds to the label ID. For example, a label ID infra can have the value aws, azure, and more. Apollo supports labels for the following resource types: Entities. Environments. Product Releases. Teams. This section will walk through the workflows related to labels and how to leverage these workflows to get the most out of Apollo.
