# Create access permission group

An access permission group may hold several assets publications of assets and several memberships of users. It may also be assigned access in several ways.

- Permanent access. This means that the access is always active until removed.
- Scheduled. Has a start and end date time. The access is active within these two points in time. It is inactive before and after.
- Reoccuring. Has a start and end date time for the re-occurance time span. It also has a re-occuring start time, end time and week days. This allows for the access to be active between 08.00 and 17.00 every monday, tuesday, friday occuring from 2020-10-01 to 2020-10-31.

To create an access permission group, you need:

- The application session token
  - [Getting an application session token](./sessionToken.md)
- The organization id
  - [Getting the organizationId](./organizationId.md)

## Create the access group with permanent access

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission-group' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "organization": "'$ORG_ID'",
  "name": "My access group no.1",
  "description": "My very first access group",
  "constraints": {}
}'
```

This will generate a response similar to:

```json
{
  "id": "dec16d14-255b-4862-8ae3-2f4209436a95",
  "name": "My access group no.1",
  "description": "My very first access group",
  "constraints": {}
}
```

Where parameter id is the access permission group id.

## Create access group with scheduled access.

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission-group' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "organization": "'$ORG_ID'",
  "name": "My access group no.1",
  "description": "My very first access group",
  "constraints": {
    "dateTimeSpanConstraint":{
      "start":"2020-11-06T02:00:00.000Z",
      "end":"2020-11-29T22:59:59.999Z"
    }
  }
}'
```

Here we add a dataTimeSpanConstraint where the access becomes active Nov 6 2020 2 AM UTC and remain active until Nov 29 2020 11 PM UTC.

## Create access group with re-occuring access.

```bash
SESSION_TOKEN="your application session token"
ORG_ID="your organization id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission-group' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "organization": "'$ORG_ID'",
  "name": "My access group no.1",
  "description": "My very first access group",
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

---

## Add asset to access group

```bash
SESSION_TOKEN="your application session token"
ACCESS_PERMISSION_GROUP_ID="access permission group id"
ASSET_PUBLICATION_ID="asset publication id"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission-group/'$ACCESS_PERMISSION_GROUP_ID'/access-permission' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "assetPublication": "'$ASSET_PUBLICATION_ID'",
  "constraints": {}
}'
```

## Add user to access group

```bash
SESSION_TOKEN="your application session token"
ACCESS_PERMISSION_GROUP_ID="access permission group id"
MEMBERSHIP_ID="id of the users membership in the organization"

curl --location --request POST 'https://api.accessy.se/asset/admin/access-permission-group/'$ACCESS_PERMISSION_GROUP_ID'/membership' \
--header 'Authorization: Bearer '$SESSION_TOKEN --header 'Content-Type: application/json' \
--data-raw '{
  "membership": "'$MEMBERSHIP_ID'"
}'
```
