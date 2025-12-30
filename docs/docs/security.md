# Security Model

The model used within the TERRA AAI, utilizing the constructs offered by the underpinning Keycloak solution facilitates the authentication and authorization needs of the TERRA platform.

Basic constructs include:

* **Clients**: Each of the TERRA components is defined as a Keycloak client. If the respective client requires to be able to contact other services on behalf of requesting parties, it is enabled the token exchange flow.
* **Client Scopes**: For each client, a client scope is created. Individual clients are configured to support available client scopes to be able to control which scopes are available per client. Scope mappers allow the exchange of requested client scopes with access token that contain the respective client as a audience. This way, access tokens generated for specific scopes can be accepted by the respective audience clients.
* **Realm Roles**: At the realm level, we define roles that can be assigned directly to users or through user groups.
* **Client Roles**: At the client level, we define roles that can be assigned directly to users or through user groups.
* **User Groups**: To facilitate the management of the user base, user groups are created to allow easier assignment of roles to users.

## Realm Roles

The currently available realm roles include:

* **terra_admin**: Reserved and assigned to adminstrators. If a user has this role associated, they should be able to perform any action.
* **terra_user**: Granted to all users of the platform. This is the base requirement for any authenticated user to utilize the application components. Without this role, the user should not be able to utilize TERRA.

More realm level roles may be created to capture more fine grained user categories.

## Client Roles

The currently available client roles include:

* **accounting.admin**: Reserved and assigned to [Accounting Service](https://terra-horizon.github.io/terra-accounting/) administrators.
* **accounting.user**: Assigned to users that should be able to access the [Accounting Service](https://terra-horizon.github.io/terra-accounting/) functionality.

More client level roles may be created to capture more fine grained user categories and component requirements.

## User Groups

The currently configured user groups include:

* **Admins**: members of this group are assigned the realm level terra_admin role
* **Users**: members of this group are assigned the realm level terra_user role
