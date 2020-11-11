# Listen to organization events

Before you continue, you will need to complete:

- [Getting an application session token](./sessionToken.md)
- [Getting the organizationId](./organizationId.md)

To listen for event related to your organization, you may do so using a web socket connection to the accessy API.

The implementation uses Stomp over web socket. In order to establish a connection and listen for events you will need:

1. Session token
2. Organization Id

You will find the web socket endpoint at

```
wss://accessy.se/ws/app
```

To connect you are required to set the Authorization header using your session token.

```
'Authorization':'Bearer <your session token>'
```

and to receive events related to your organization, you subscripe to

```
/topic/organization/<organization id>
```

If you want to explore the events received, you may download this tool [Accessy Stomp Client](StompClient.jar) (Requires java to run)
You start the Stomp Client by typing:

```
java -jar StompClient.jar <ORG ID> <SESSION_TOKEN>
```

## EVENT TYPES

### MEMBERSHIP_CREATED

Received when a user becomes a member of your organization. If the user has been invited, you use the parameter "invitationId" to match with previous invite.
See [Create invitation](createInvitation.md) for how to invite a user.

```json
{
  "userId": "7c0e1673-43a6-40ab-afa5-3061915e56fb",
  "organizationId": "679716c6-426a-4752-9562-0e0e4d4e4c47",
  "invitationId": "b041c925-f17e-4d02-bd37-bdd092f40aa1",
  "role": "USER",
  "requestingUserSuperAdmin": false,
  "metaData": {
    "created": "2020-11-09T16:30:08.564135Z",
    "organizationId": "679716c6-426a-4752-9562-0e0e4d4e4c47"
  },
  "eventType": "MEMBERSHIP_CREATED"
}
```
