# Api Examples

## Client Secret

A client registered in the TERRA AAI can request to be issued an access token by which it can authenticate its calls to other services. In order to do that, it needs to have the clientId and clientSecret that was assigned to it through the TERRA AAI registration of the client.

This authorization flow is called Client Credentials and is defined by the OIDC standard.

```console
curl --location 'https://<TERRA_AAI_DOMAIN>/oauth/realms/<REALM>/protocol/openid-connect/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=client_credentials' \
--data-urlencode 'client_id=<CLIENT_ID>' \
--data-urlencode 'client_secret=<CLIENT_SECRET>' \
--data-urlencode 'scope=<SCOPE>'
```

