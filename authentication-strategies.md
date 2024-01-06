1. **Basic Authentication**

   Basic Authentication is a simple authentication scheme built into the HTTP protocol. The client sends HTTP requests with the Authorization header that contains the word Basic followed by a space and a base64-encoded string username:password. For example:

   ```
   Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
   ```

   **Pros:** Easy to implement.

   **Cons:** Credentials sent over the network are encoded with Base64, but they are not encrypted or hashed in any way. It is not secure to use without HTTPS.

2. **Session Based Authentication**

   In session-based authentication, the server will create a session for the user after the user logs in. The session id is then stored on a cookie on the user's browser. While the user stays logged in, the cookie would be sent along with every subsequent request. The server can then compare the session id stored on the cookie against the session information stored in the memory to verify user's identity and sends response with the corresponding state.

   **Pros:** Simple to use; the HTTP protocol doesn't maintain state.

   **Cons:** Does not scale well because sessions are stored in server memory, and an increase in session volume can affect performance.

3. **Token Based Authentication**

   Token-based authentication is stateless. The server creates a JWT with a secret and sends the JWT to the client. The client stores the JWT (usually in local storage) and includes JWT in the header with every request. The server would then validate the JWT with every request from the client and sends response.

   **Pros:** Stateless, and hence more scalable than session-based authentication. Works well with mobile and web applications.

   **Cons:** Tokens can be stolen, so we need to store them securely.

4. **JWT (JSON Web Token) Authentication**

   JWT is a token format. It is a self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

   **Pros:** Compact, self-contained, works well with CORS, and can be used across different domains.

   **Cons:** Token size can be large and might affect performance. Also, the payload is just Base64Url encoded, which can be easily decoded and read. So, don't put sensitive data in the JWT payload.

5. **OAuth**

   OAuth is a protocol that lets external apps request authorization to private details in a user's account without getting their password. This is preferred over Basic Authentication because tokens can be limited to specific types of data, and can be revoked by users at any time.

   **Pros:** Allows third-party services to use account information without the need to share password. Provides granular access to resources.

   **Cons:** Can be complex to implement.

6. **SSO (Single Sign-On)**

   SSO is a session and user authentication service that permits a user to use one set of login credentials (e.g., name and password) to access multiple applications. The service authenticates the end user for all the applications the user has been given rights to and eliminates further prompts when the user switches applications during the same session.

   **Pros:** Improves user experience by requiring only one set of credentials to access multiple applications.

   **Cons:** If the primary login is compromised, all applications that use SSO are at risk.