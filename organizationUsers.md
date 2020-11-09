# List users in an organization

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting the organizationId](./organizationId.md)

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"

curl --location --request GET 'https://api.accessy.se/asset/admin/organization/'$ORG_ID'/user' \
--header 'Authorization: Bearer '$SESSION_TOKEN
```

This will generate paginated result similar to the following:

```json
{
  "items": [
    {
      "id": "a497bfd6-a3d3-43db-92c5-070884c85d6d",
      "firstName": "Application",
      "lastName": "My Application Credentials",
      "uiLanguageCode": "en",
      "application": true
    },
    {
      "id": "7bd2441f-f10a-4d75-98bd-ad6f6411257c",
      "firstName": "Lisa",
      "lastName": "Lawson",
      "msisdn": "+467356....6",
      "uiLanguageCode": "en",
      "application": false
    }
  ],
  "totalItems": 2,
  "pageSize": 25,
  "pageNumber": 0,
  "totalPages": 1
}
```

If the parameter "application" has the value true, then this is not a user, but application credentials.
