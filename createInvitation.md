# Create invitations to the organization

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting the organizationId](./organizationId.md)

Sending invitations to people requires you to provide the api call with their cell phone numbers in an international formatted string (MSISDN) e.g. "+46123123456"

The user receives the invitation as a text message with a link to https://accessy.se/invite where instructions on how to donwload the Accessy app is provided.

If the user already has the app installed, a notification will be sent and the user may open the app and accept or reject the invitation.

**Please note**

This call requires you to use the Accept header to set version v2.

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"

curl --location --request POST 'https://api.accessy.se/org/admin/organization/'$ORG_ID'/invitation' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' --header 'Accept: application/vnd.axessions.v2+json' \
--data-raw '{
"message": "hey handsome, join us",
"msisdns": ["+46123123456"]
}'
```

This will generate a result similar to the following:

```json
[
  {
    "id": "9d08f2db-3e06-40af-8f02-9c957e76e6af",
    "organization": {
      "id": "679716c6-426a-4752-9562-0e0e4d4e4c47",
      "name": "My Organisation",
      "orgNumber": "357363563",
      "vatNumber": "2525253",
      "domainDataEndpoint": "http://rec/rec",
      "phoneNumber": "x",
      "billingAddress": {
        "id": "f324ddf6-ed18-4df9-be3d-93fb3a18517a",
        "contact": "x",
        "apartmentOrSuite": "x",
        "street": "x",
        "zip": "x",
        "city": "x",
        "province": "x",
        "country": "x"
      },
      "membershipRequestsEnabled": false
    },
    "recipientMsisdn": "+46123123456",
    "invitationMessage": "hey handsome, join us",
    "status": "PENDING",
    "senderName": "Application Example Application Credentials",
    "createdAt": "2020-11-09T11:55:28.804Z",
    "createdByApplication": true
  }
]
```

This is quite verbose, but the important parameter is the id.
This is the invitation Id and will be present in the event generated when the user accepts the invitation. See [Listen for organization events](listenForOrganizationEvents.md)
