---
source_url: "https://www.palantir.com/docs/foundry/custom-docs/add-images/"
title: "Add images or media to custom docs"
---
# Add images or media to custom docs

You can use standard Markdown syntax to reference an image file in your documentation repository and display the image in custom docs. The standard Markdown syntax for referencing an image looks as follows:  There are several ways of storing images so that they can be referenced by a custom documentation page. We recommend avoiding the use of large GIFs or videos, as they can be difficult to follow and can cause performance issues in the documentation. Images stored in the Foundry filesystem. To reference an image in a documentation repository, you can upload the file to the Palantir platform directly and use a Blobster link. First, upload your image to the Palantir platform via the Foundry filesystem. After the image has been uploaded as a resource in the platform, navigate to the resource, then right-click and select Copy Image Address. This address should be formatted <enrollment_url>/blobster/api/salt/<blobster_rid>. Use this as the address when referencing the image in Markdown as follows.  Images stored as dataset files. You can also use a dataset file image reference in custom documentation.
