# List assets in an organization

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting the organizationId](./organizationId.md)

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"

curl --location --request GET 'https://api.accessy.se/asset/admin/organization/'$ORG_ID'/asset' \
--header 'Authorization: Bearer '$SESSION_TOKEN
```

This will generate paginated result similar to the following:

```json
{
  "items": [
    {
      "id": "469bc4ce-9c9a-487c-9284-5468ab05c4df",
      "createdAt": "2020-11-07T07:22:33.176Z",
      "updatedAt": "2020-11-07T07:33:21.256Z",
      "name": "My Entrance",
      "description": "",
      "position2d": {
        "longitude": 13.0007497,
        "latitude": 55.5996943
      },
      "additionalDeviceAuthentication": "NONE",
      "address": {
        "id": "95d7c088-3905-4980-95cc-af5206b5b707",
        "country": "Sweden",
        "city": "Malmö",
        "zipCode": "21142",
        "street": "Storgatan 22A"
      },
      "images": [
        {
          "id": "72eb49af-ad45-474f-852d-b1a301b6b93a",
          "imageId": "8c8db4c8-60c7-4b59-9b94-ba959426d378",
          "thumbnailId": "9fde2a5c-ceac-42e9-a256-48f9c76441e0",
          "size": 62109,
          "width": 662,
          "height": 372,
          "mainImage": false
        }
      ],
      "roomType": "Entrance",
      "allowGuestAccess": true
    }
  ],
  "totalItems": 1,
  "pageSize": 25,
  "pageNumber": 0,
  "totalPages": 1
}
```

Short description of parameters:

- "id" The asset id.
- "name" The name of the asset.
- "roomType" Indicates what kind of asset this is.
- "allowGuestAccess" If true, guest access may be issued for this asset.
- "additionalDeviceAuthentication" If "PIN_CODE" then user need to enter app pin code in order to use any operations of this asset.
