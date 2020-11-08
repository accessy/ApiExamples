# Using the Accessy Api

This is a tutorial of how to use the Accessy API with real life examples to complement the api documentation (https://api.accessy.se). 
In order to use it, you will need to request application credentials for you organization.
You request this by sending us an email at support@accessy.se. 

In your application credentials, you will find two parameters:
- client id
- client secret

You use these two in order to get your access token. The access token is required to call the api.


## Get the application session token
Ref: https://api.accessy.se/doc/#tag/Authentication

```bash
curl -s --location --request POST 'https://api.accessy.se/auth/oauth/token' \
--header 'Content-Type: application/json' \
--data-raw '{
    "audience": "https://api.accessy.se",
    "grant_type": "client_credentials",
    "client_id": "'$CLIENT_ID'",
    "client_secret": "'$CLIENT_SECRET'"
}'
```

```json
{
    "access_token": "ey...pA",
    "token_type": "Bearer",
    "expires_in": "604800000"
}
```
