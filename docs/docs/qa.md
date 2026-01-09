# Quality Assurance

Key aspects of the Quality Assurance checklist that TERRA services must pass have been defined in the processes and documents governing the platform development and quality assurance. 

For the case of TERRA AAI we rely on the the [Keycloak](https://www.keycloak.org/) Identity and Access Management solution which is a well established and widely used [open source](https://github.com/keycloak/keycloak) project.

In the context of TERRA we apply the needed configuration utilizing the available features in Keycloak without any customizations that would jeopartize the security and offered service quality. 

## Smoke testing

In the context of the TERRA usage and the flows presented in the [Architecture Overview](architecture.md), a smoke test scenario is available for evaluation under the respective [Testing Automations](automations.md). These smoke test scenarios cover the following grant flows:

* [User Password](token-user-password.md)
* [Client Secret](token-client-secret.md)
* [Refresh Token](token-refresh-token.md)
* [Token Exchange](token-exchange-token.md)
 
The test scripts can be found in the service [code repository](https://github.com/terra-horizon/terra-aai/tree/main/tests)
