# Using the Accessy Api

This is a tutorial of how to use the Accessy API. In order to use it, you will need to request application credentials for you organization.
You request this by sending us an email at support@accessy.se. 

In your application credentials, you will find two parameters:
- client id
- client secret

You use these two in order to get your access token. The access token is required to call the api.


## Get the application session token
Ref: https://api.accessy.se/doc/#tag/Authentication


```json
{
    "access_token": "ey...pA",
    "token_type": "Bearer",
    "expires_in": "604800000"
}
```
