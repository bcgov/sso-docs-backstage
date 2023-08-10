---
sidebar_position: 5
---

# Installation JSON file and Identity Providers

---

## Installation JSON

Once your request has been completed, you will be able to download your installation file for each environment. It includes the client information to set up your SSO configuration.

The main difference between `confidential` and `public` clients is that confidential clients require client secret

An example Installation JSON for `public` client type
```json
{
  "realm": "<standard_realm_name>",
  "auth-server-url": "https://<env>.loginproxy.gov.bc.ca/auth/",
  "ssl-required": "external",
  "resource": "<client_id>",
  "public-client": true,
  "verify-token-audience": true,
  "use-resource-role-mappings": true,
  "confidential-port": 0
}
```

An example Installation JSON for `confidential` client type
```json
{
  "realm": "<standard_realm_name>",
  "auth-server-url": "https://<env>.loginproxy.gov.bc.ca/auth/",
  "ssl-required": "external",
  "resource": "<client_id>",
  "credentials": {
    "secret": "<client_secret>"
  },
  "confidential-port": 0
}
```

## Specifying an identity provider (IDP) to bypass the Keycloak login page

If there is more than one IDP in the realm, the Keycloak server directs your users into a login page to let them choose the IDP that they want to authenticate with. It is possible to skip the login page or override the default IDP in Keycloak by passing the optional query param" kc_idp_hint". [List of kc_idp_hints here](https://github.com/bcgov/sso-keycloak/wiki/Using-Your-SSO-Client#do-skip-the-keycloak-login-page)

If using an adapter, there is an option for providing `idpHint`, and
if not, please specify it in the `Authorization URL` in your code or configuration, i.e.`http://localhost:8080/auth?kc_idp_hint=<idp_name>`
Please see [here](https://www.keycloak.org/docs/latest/server_admin/index.html#_client_suggested_idp) for more detail.

If the framework you are using prevents you from being able to pass through the _IDP hint_, please reach out to our team through rocket chat or email to ask about alternative options.