# Create guest access

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting a user's membership id](./organizationMembership.md)
- [Getting an asset's publications](./organizationAssetPublications.md)

Guest access allow you to grant access to people who is not part of your organization.
When creating a guest access from the Accessy API, you will in return get a URL. This URL may be distributed via email or meeting invitations. **Anyone with access to the URL will have access to open a door or what the assets may control!**
Because of this low level security, the asset must be configured to allow guest access.

The guest access may contain access to one or several asset publications.

When creating a guest access you point to a membership id, this id should represent the user who invite guests. This user's name will be presented to guests that use the URL.

**Guest access may only be issued with a start time and end time that spans over 12 hours at maximum.**

```bash
SESSION_TOKEN="your application session token"
USER_MEMBERSHIP_ID="the membership id of the user inviting guests"
ASSET_PUBLICATION_ID="your asset publication id"

curl --location --request POST 'https://api.accessy.se/asset/admin/guest-access' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
	"name": "Welcome",
	"message": "",
	"startTime": "2020-11-11T18:00:00.000Z",
	"endTime": "2020-11-11T22:00:00.000Z",
	"onBehalfOfMembershipId": "'$USER_MEMBERSHIP_ID'",
	"assetPublicationIds": ["'$ASSET_PUBLICATION_ID'"]
}'
```

This will generate a URL similar to:
https://guest.accessy.se/guest-access/83OCxB7W50C4puf6Zkr57QRycXtu33a519TmtdX1o1zGoP16rh61
