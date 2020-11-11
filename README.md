# Using the Accessy Api

This is a tutorial of how to use the Accessy API with real life examples to complement the api documentation (https://api.accessy.se).
The examples are using curl commands to be independant of programming languages.

## Basics

In order to use the Accessy API, you will need to request application credentials for you organization.
You request this by sending us an email at support@accessy.se.

### Application session token

Next you will need to get an application session token

[Getting an application session token](./sessionToken.md)

### The data model

Before you get to the part of assigning access, you need to understand how you retreive information about membership and asset publications.

![alt text](https://raw.githubusercontent.com/accessy/ApiExamples/main/images/SimpleDataModel.png "A simplified data model")
The above simplified data model visualize the relationship between entities exposed by the API.

**Organization**

This is the organization that your application credentials are issued from. Application credentials can only operate on a single organization.

**User**

Represents a registered user to Accessy.

**Membership**

When a user becomes part of an organization, this is established through a membership.

**Asset**

This is a representation of something that requires access to operate. It could be a conference room that is using a door lock to control physical access.

**Asset Publication**

When an asset is available to an organization, this is established through a publication.

**Access Permission**

To grant a user access to an asset, this is accomplished through using the asset publication and the users membership as reference.

### Organization id

The application credentials is issued by an organization and only one organization.
The id of the organization need to provided by several API calls.

[Getting the organizationId](./organizationId.md)

### Organization users

The organization may have users as members through membership.

[Getting a list of users in an organization](./organizationUsers.md)

If you know the user, you may lookup the membership. This will be needed when you refer to a user within the organization.

[Getting a user's membership id](./organizationMembership.md)

### Organization assets

The organization may have assets published to it. Either by the organization itself or by 3rd part organizations.

[Getting a list of assets](./organizationAssets.md)

If you know the id of the asset, you may lookup the asset publication. this will be needed referring to the asset when assigning access to the asset.

[Getting an asset's publications](./organizationAssetPublications.md)

---

## Assign access

Assigning access of an asset may be done in two ways.

1. Assign personal access: [Create Access Permission](./createAccessPermission.md)
2. Add user to an access group [Create access group](./createAccessPermissionGroup.md)

---

## Invite user to become a member of the organization

You may invite users to become members to your organization.

Invite user: [Create invitation](./createInvitation.md)

## Issue guest access

Guest access allows you to generate a weblink with access to assets.  
[Create guest access](./createGuestAccess.md)

## Listen to organization events

You can receive events from Accessy API.
[Listen to organization events](./listenForOrganizationEvents.md)
