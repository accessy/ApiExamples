# Using the Accessy Api

This is a tutorial of how to use the Accessy API with real life examples to complement the api documentation (https://api.accessy.se).
The examples are using curl commands to be independant of programming languages. 

In order to use the Accessy API, you will need to request application credentials for you organization.
You request this by sending us an email at support@accessy.se. 

In your application credentials, you will find two parameters:
- client id
- client secret

You use these two in order to get your access token. The access token is required to call the API.


## Get the application session token

### PLEASE NOTE! 
**Always make this call from your protected server-side code.
Always get the session token server-side and pass the session token to your client. Store your credentials (client id and client secret) in a secure environment, anyone with access to your credentials may administrate your organization!
Never store your credentials in a client application, such as web or mobile application, anyone with the access to the client may gain access to your credentials!**

Ref: https://api.accessy.se/doc/#tag/Authentication

To get your session token, you make the following POST:
```bash
CLIENT_ID="<your client id>"
CLIENT_SECRET="<your client secret>"

curl -s --location --request POST 'https://api.accessy.se/auth/oauth/token' \
--header 'Content-Type: application/json' \
--data-raw '{
    "audience": "https://api.accessy.se",
    "grant_type": "client_credentials",
    "client_id": "'$CLIENT_ID'",
    "client_secret": "'$CLIENT_SECRET'"
}'
```
This will generate an answer similar to the following:
```json
{
    "access_token": "ey...pA",
    "token_type": "Bearer",
    "expires_in": "604800000"
}
```
The parameters "token_type" and "access_token" are used to compose the header to use for authorization (Authorization: Bearer ey...pA) 
The parameters "expires_in" is the time in millisconds before it expires. 





