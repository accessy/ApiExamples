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
