# List asset publications for an asset in an organization

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting the organizationId](./organizationId.md)
- [Getting a list of assets](./organizationAssets.md)

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"
ASSET_ID="your asset id"

curl --location --request GET 'https://api.accessy.se/asset/admin/organization/'$ORG_ID'/asset/'$ASSET_ID'/asset-publication' \
--header 'Authorization: Bearer '$SESSION_TOKEN
```

This will generate paginated result similar to the following:

```json
{
  "id": "263532cc-653d-4f9a-aa34-98f0c29d9d89",
  "fromOrganization": "679716c6-426a-4752-9562-0e0e4d4e4c47",
  "toOrganization": "679716c6-426a-4752-9562-0e0e4d4e4c47",
  "listingState": "UNLISTED"
}
```

Short description of parameters:

- "id" The asset publication id.
- "fromOrganization" The id of the organization that published the asset.
- "toOrganization" The id of the organization that received the asset publication.
- "listingState" an enumeration that indicates the following:

  - Unlisted visibility means that this asset will not be listed when searching. Delegators may assign access to users, but users may not request access.

  - Organization visibility means that this asset will be listed to members of the organization when searching, and users may request access. Delegators can then approve the request. Delegator may also assign access to users.

  - Public visibility means that this asset will be listed in public for any user when searching. Users may request access. Delegators can then approve the request. Delegator may also assign access to users.
