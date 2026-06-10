---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/get-profile-picture-of-user/"
title: "Get Profile Picture Of User \u2022 API Reference"
---
# Get Profile Picture Of User

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getProfilePictureOfUser

**path:** /api/v2/admin/users/{userId}/profilePicture

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| userId | stringType | True | A Foundry User ID. |

### Response

#### Body

The user's profile picture in binary format. The format is the original format uploaded by the user. 
The response will contain a `Content-Type` header that can be used to identify the media type.

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| InvalidProfilePicture | The user's profile picture is not a valid image |
| ProfileServiceNotPresent | The Profile service is unexpectedly not present. |
| UserDeleted | The user is deleted. |
| GetProfilePictureOfUserPermissionDenied | Could not profilePicture the User. |
| UserNotFound | The given User could not be found. |
