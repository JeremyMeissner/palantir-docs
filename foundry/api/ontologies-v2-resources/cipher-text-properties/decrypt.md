---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/cipher-text-properties/decrypt/"
title: "Decrypt \u2022 API Reference"
---
# Decrypt

## Endpoint

Decrypt the value of a ciphertext property.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.decrypt

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/ciphertexts/{property}/decrypt

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |
| primaryKey | stringType | True | The primary key of the object with the CipherText property. |
| property | stringType | True | The API name of the CipherText property. To find the API name for your CipherText property, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Response

#### Body

Success response.

**name:** DecryptionResult

**example:** {"plaintext":"Jane Doe"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| plaintext | stringType | False |  |

**example:** {"plaintext":"Jane Doe"}
