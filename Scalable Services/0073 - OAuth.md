**OAuth**

OAuth (Open Authorization) is an open standard protocol for authorization that allows third-party applications to access user resources on a server without sharing user credentials.

**Key Concepts:**

1. **Roles in OAuth:**

   * **Resource Owner:** The user who owns the data or resource.
   * **Client:** The application requesting access to the user’s resources.
   * **Authorization Server:** Issues access tokens after authenticating the resource owner and obtaining consent.
   * **Resource Server:** Hosts the protected resources and validates access tokens.

2. **OAuth Flow:**

   * The client requests authorization from the resource owner.
   * If approved, the authorization server issues an authorization grant.
   * The client exchanges the grant for an access token.
   * The client uses the access token to access protected resources on the resource server.

3. **Types of Authorization Grants:**

   * **Authorization Code Grant:** Used by web and mobile apps; involves redirection and exchanging an authorization code for tokens.
   * **Implicit Grant:** Simplified flow for browser-based apps, less secure and being deprecated.
   * **Resource Owner Password Credentials Grant:** Uses user credentials directly; discouraged due to security risks.
   * **Client Credentials Grant:** For machine-to-machine authentication without user involvement.
   * **Device Authorization Grant:** For devices with limited input capabilities.

4. **Access Tokens:**

   * Short-lived tokens used by clients to access protected resources.
   * Usually JWTs or opaque tokens.

5. **Refresh Tokens:**

   * Long-lived tokens used to obtain new access tokens without user involvement.

**Use Cases:**

* Allowing third-party apps to access user data on platforms like Google, Facebook, or GitHub without sharing passwords.
* Securing APIs by validating access tokens.

OAuth focuses on delegated authorization, not authentication (which is handled by protocols like OpenID Connect built on top of OAuth). It is widely used in microservices for secure and scalable authorization management.
