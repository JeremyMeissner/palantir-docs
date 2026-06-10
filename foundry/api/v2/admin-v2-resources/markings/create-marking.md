---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/markings/create-marking/"
title: "Create Marking"
---
# Create Marking

Creates a new Marking. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Request body. The initial roles that will be assigned when the Marking is created. At least one ADMINISTER role must be provided. This can be changed later through the MarkingRoleAssignment operations. WARNING: If you do not include your own principal ID or the ID of a Group that you are a member of, you will create a Marking that you cannot administer. Users and Groups that will be able to view resources protected by this Marking. This can be changed later through the MarkingMember operations. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". Response body. The created Marking. The ID of a security marking. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". If this marking is associated with an Organization, its RID will be populated here. The time at which the resource was created. The Foundry user who created this resource. Examples. Error responses.
