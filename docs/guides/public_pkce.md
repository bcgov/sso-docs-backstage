---
sidebar_position: 4
---

# Public Client

---

## Proof Key for Code Exchange (PKCE)

The javascript adapter for keycloak has built-in support for using PKCE. See the documentation under the init method here, specifically the `pkceMethod`. For example, when initializing the adapter you can call `keycloak.init({ pkceMethod: 'S256' })` to use PKCE. Use the 'S256' method for you public client.

If not using the adapter, you can use a custom implementation. This will require 4 steps:

Create a `code_verifier` (cryptographically secure string)
Hash the code verifier with the SHA256 method to create a `code_challenge`
Send the code challenge and code challenge method (S256) as query parameters when redirecting users to the authorization endpoint
When exchanging the received code for an access token, send the initial `code_verifier` to ensure your application initiated the current exchange.
For an example of a custom PKCE implementation, see here for generating the authentication URL and [here](https://github.com/bcgov/sso-requests/blob/dev/app/utils/openid.ts#L49) for exchanging the received code for an access token.

Learn More [OIDC & PKCE](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow-with-proof-key-for-code-exchange-pkce)

## Public Clients, Redirect URIs and Web Origins

The redirect URIs will be copied over to Keycloak Web Origins setup. In addition, adding ‘+’ to permit all origins of Valid Redirect URIs