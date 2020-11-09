# Create access permission

Assigning access of an asset to a user can be done in several ways.

Permanent access. This means that the access is always active until removed.
Scheduled. Has a start and end date time. The access is active within these two points in time. It is inactive before and after.
Reoccuring. Has a start and end date time for the re-occurance time span. It also has a re-occuring start time, end time and week days. This allows for the access to be active between 08.00 and 17.00 every monday, tuesday, friday occuring from 2020-10-01 to 2020-10-31.

To create an access permission for a user and an asset, you need:

- The application session token
  - [Getting an application session token](./sessionToken.md)
- The membershipId of the user in the organization.
  - [Getting a user's membership id](./organizationMembership.md)
- The asset publication id of the asset.
  - [Getting an asset's publications](./organizationAssetPublications.md)

## Permanent access

```bash
SESSION_TOKEN="your application session token"
USER_MEMBERSHIP_ID="users membership id"
ASSET_PUBLICATION_ID="asset publication id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "membershipId": "'$USER_MEMBERSHIP_ID'",
  "assetPublicationId": "'$ASSET_PUBLICATION_ID'",
  "constraints": {}
}'
```

As we haven't defined any constraints in the example above, this access permission is considered permanent and will be active until removed.

## Scheduled access

```bash
SESSION_TOKEN="your application session token"
USER_MEMBERSHIP_ID="users membership id"
ASSET_PUBLICATION_ID="asset publication id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "membershipId": "'$USER_MEMBERSHIP_ID'",
  "assetPublicationId": "'$ASSET_PUBLICATION_ID'",
  "constraints": {
    "dateTimeSpanConstraint":{
      "start":"2020-11-06T02:00:00.000Z",
      "end":"2020-11-29T22:59:59.999Z"
    }
  }
}'
```

Here we add a dataTimeSpanConstraint where the access becomes active Nov 6 2020 2 AM UTC and remain active until Nov 29 2020 11 PM UTC.

## Re-occuring access

```bash
SESSION_TOKEN="your application session token"
USER_MEMBERSHIP_ID="users membership id"
ASSET_PUBLICATION_ID="asset publication id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "membershipId": "'$USER_MEMBERSHIP_ID'",
  "assetPublicationId": "'$ASSET_PUBLICATION_ID'",
  "constraints": {
    "dateTimeSpanConstraint":{
      "start":"2020-11-06T02:00:00.000Z",
      "end":"2020-11-29T22:59:59.999Z"
    },
    "dayTimeSpanConstraint":{
      "daysOfWeek":["MONDAY","TUESDAY","WEDNESDAY"],
      "startTime":"07:00",
      "endTime":"23:59"
    }
  }
}'
```

As we also added a dayTimeSpanConstraint the access becomes active monday, tuesday and wednesday between 7:00 AM and 23:59 PM within the period of Nov 6 2020 2 AM UTC and Nov 29 2020 11 PM UTC. Otherwise the access is not active.
