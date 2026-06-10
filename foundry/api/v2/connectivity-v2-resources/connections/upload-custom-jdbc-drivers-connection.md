---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/connections/upload-custom-jdbc-drivers-connection/"
title: "Upload Custom Jdbc Drivers Connection"
---
# Upload Custom Jdbc Drivers Connection

Upload custom jdbc drivers to an existing JDBC connection. The body of the request must contain the binary content of the file and the Content-Type header must be application/octet-stream. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-connection-write. Path parameters. The Resource Identifier (RID) of a Connection (also known as a source). Query parameters. The file name of the uploaded JDBC driver. Must end with .jar. Request body. Response body. The Resource Identifier (RID) of a Connection (also known as a source). The unique resource identifier (RID) of a Folder. The display name of the Connection. The display name must not be blank. The export settings of a Connection. The worker of a Connection, which defines where compute for capabilities are run. Examples. Error responses.
