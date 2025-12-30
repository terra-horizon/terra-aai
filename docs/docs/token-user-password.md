# Api Examples

## User Password

A user registered in the TERRA AAI that can be authenticated with a username and password can request to issue an access token by which is can authenticate its calls to TERRA services. In order to do that, they need to have the username and password that was provided to the TERRA AAI registration of the user.

This authorization flow is called the Resource Owner Password Flow and is defined by the OIDC standard.

```console
curl --location 'https://<TERRA_AAI_DOMAIN>/oauth/realms/<REALM>/protocol/openid-connect/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=password' \
--data-urlencode 'client_id=<CLIENT_ID>' \
--data-urlencode 'username=<USERNAME>' \
--data-urlencode 'password=<USER_PASSWORD>' \
--data-urlencode 'scope=<SCOPE>'
```

This flow cannot be used with identity federation authentication flows. The code flow which is used to authenticate users in the TERRA platform through identity federation requires user interaction and redirects that cannot be demonstrated through a console curl example.

