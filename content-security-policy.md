Content Security Policy (CSP) is a security standard introduced to prevent cross-site scripting (XSS), clickjacking, and other code injection attacks resulting from the execution of malicious content in the trusted web page context. It provides a standard method for website owners to declare approved origins of content that browsers should be allowed to load on a website.

How it works and its purpose:

1. **Purpose of CSP:** The primary purpose of CSP is to mitigate and report XSS attacks. XSS attacks exploit the browser's trust in the content received from the server. Malicious scripts are executed in the victim's browser, which can then be used to steal sensitive information like passwords and credit card numbers.

2. **How CSP Works:** CSP works by defining a whitelist of content sources which are trusted. For each type of content, the server can specify a policy, indicating which domains are a valid source of executable scripts. A CSP compatible browser will then only execute scripts loaded in source files received from those whitelisted domains, ignoring all other script (inline and external).

3. **Implementing CSP:** CSP is implemented through a special HTTP header that the server returns with the resources it serves. This header is called "Content-Security-Policy". The value of this header is the policy, and dictates what resources the user agent is allowed to load for that page.

4. **CSP Directives:** CSP uses directives to establish the rules for loading different types of resources. For example, the `default-src` directive sets the default policy for fetching resources. The `script-src` directive defines the allowed sources for JavaScript. There are many other directives for other types of resources, like `img-src`, `style-src`, `font-src`, etc.

5. **CSP Reporting:** CSP also includes a reporting feature that can alert developers when certain policies are violated. This is done using the `report-uri` directive, which specifies a URL where the reports about policy violation are sent.

6. **Nonce and Hashes in CSP:** To allow specific inline scripts or styles, you can use a nonce (a random string that is generated for each request) or a hash of the script or style block. You add the nonce or hash to the CSP header, and also to the script or style block in your HTML.

7. **CSP and Inline Scripts:** By default, CSP does not allow inline scripts. This is because an attacker could inject a script tag directly into your page. To enable inline scripts, you can use a nonce or a hash to allow specific script blocks.

8. **CSP Level 2 and 3:** CSP Level 2 and 3 introduced several new features and directives, such as `frame-ancestors` to control embedding, `form-action` to control where forms can be submitted, and `upgrade-insecure-requests` to upgrade HTTP requests to HTTPS.

So, CSP is a powerful security feature that helps to detect and mitigate certain types of attacks, including XSS and data injection attacks. It works by specifying an HTTP header that lists valid source hosts for embedded content on a website.