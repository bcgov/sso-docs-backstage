---
sidebar_position: 11

---

# Our Guidance: Skip keycloak login page

---
Recommend Skipping the Keycloak Login Page and if you ABSOLUTELY need it

### Read On
As you've read in our guidance in setting up a keycloak client do's and don'ts here, our recommendation is to skip the keycloak login page ie

In KeyCloak, if the realm that contains your client has more than one IDP configured, KeyCloak shows a page that prompts the user to select which IDP they want to log in with. Almost all teams have chosen to hide this page from their users by specifying the IDP as a query string parameter in the KeyCloak Authorization URI value behind their login button. The query string is 'kc_idp_hint'. (The IDPs available will depend on the standard realm in which your client exists.) By specifying the IDP in this way, the user will be redirected directly to the login page for the identity provider and will not see the KeyCloak login choice page at all.


## but if you need it, please specify dedicated text for login page

If you are a client of ours and have an absolute need to have a dedicated set of text for your login page, through our app, you can specify the text under the field setting Keycloak Login Page Name

![Private vs Confidential](login_title_august2023.png)
