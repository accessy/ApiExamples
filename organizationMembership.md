# Show the membership of a user in an organization

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting the organizationId](./organizationId.md)
- [Getting a list of users in an organization](./organizationUsers.md)

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"
USER_ID="user id of the user to get the membership for"

curl --location --request GET 'https://api.accessy.se/asset/admin/user/'$USER_ID'/organization/'$ORG_ID'/membership' \
--header 'Authorization: Bearer '$SESSION_TOKEN
```

This will generate a result similar to the following:

```json
{
  "id": "8fc26e61-3263-4ffb-a915-1830c937151d",
  "userId": "7bd2441f-f10a-4d75-98bd-ad6f6411257c",
  "organizationId": "679716c6-426a-4752-9562-0e0e4d4e4c47",
  "roles": [
    "ASSET_ADMINISTRATOR",
    "DEVICE_ADMINISTRATOR",
    "REALESTATE_ADMINISTRATOR",
    "USER",
    "ORGANIZATION_ADMINISTRATOR"
  ]
}
```

The parameter "id" is the membership id for the user in the organization.
The parameter "roles" is an enumeration of what roles has been assigned to the user in the organization.
