---
source_url: "https://www.palantir.com/docs/gotham/api/general/overview/getting-started/"
title: "Getting started \u2022 API Reference"
---
To make API calls, please follow the subsequent steps.

1. [Find your hostname](#find-your-hostname)
2. [Get an authentication token](#get-an-authentication-token)
3. [Make a request](#make-a-request)

## Find your hostname

The hostname is present in all URLs when accessing Palantir applications through the user interface.
Find your hostname from your browser's URL address bar while logged into Palantir.
The hostname should look like the following: `https://<hostname>/`.

## Get an authentication token

Follow the steps in [Authentication](/docs/gotham/api/general/overview/authentication/) to get an authentication token.

## Make a request

After getting your hostname and authentication token, you can use API clients to interact with the API.

All API calls to Gotham API should use HTTPS and the hostname for the particular instance.

### Example Requests

- [cURL](#using-curl)

#### Using cURL

Run the following to call the *get object** endpoint to get information a specific object with ID `ri.gotham.111111-0.object-internal.111111`:

```bash
curl -H "Authorization: Bearer <your token>" \
 "https://<hostname>/api/gotham/v1/objects/ri.gotham.111111-0.object-internal.111111"
```

To send a POST request, use the `-d` flag to include a POST body and be sure to set a `Content-type` of `application/json`.

Run the following to call the **create object** endpoint and create a new object of type `com.palantir.object.person`.

```bash
curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer <your token>" \
 "https://<hostname>/api/gotham/v1/objects/types/com.palantir.object.person" \
 -d '{"title": "Anna Smith-Doe"}'
```

#### OpenAPI Compatibility

This API is available as an OpenAPI-compliant definition.  The definition download is available at the following URL:

```bash
curl -H "Authorization: Bearer <your token>" \
 "https://<hostname>/api/gotham/openapi"
```

[Authentication](/docs/gotham/api/general/overview/authentication/) is required to access the OpenAPI definition.

:::callout{theme=warning title=Warning}
The downloadable definition has been compatibility-tested with the Open Source [OpenAPI Java client generator using Jersey2 Library](https://openapi-generator.tech/docs/generators/java).
Usage of other languages and/or libraries and their compatibility is the responsibility of API consumers.

Structure of downloaded OpenAPI definition is subject to change between releases.
Existing consumers of OpenAPI-generated client code are subject to general compatibility guarantees as described in [versioning](/docs/gotham/api/general/overview/versioning/).
:::

Additional information about OpenAPI Generator is available [here](https://openapi-generator.tech/).
