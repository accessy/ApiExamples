# Get the organization id

You will need your application session token before you continue. Instructions found here: [Getting an application session token](./sessionToken.md)

```bash
SESSION_TOKEN="your application session token"

curl -s --location --request GET 'https://api.accessy.se/asset/user/organization-membership' --header 'Authorization: Bearer '$SESSION_TOKEN
```

This will generate an answer similar to the following:

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

The parameter "organizationId" is the id of the organization.
The parameter "roles" is an enumeration of what roles has been assigned to the application credentials used.
