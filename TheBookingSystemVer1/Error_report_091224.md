These were the errors I got in the ZAP report:

Format String Error - (Medium) - amount: 1
- This error occurs when the submitted data of an input string is evaluated as a command by the application. It could be fixed by deleting bad character strings, which would require recompiling of the background executable.

Cross Site Scripting Weakness (Persistent in JSON Response) - (Low) - amount: 2
- This error was found in a JSON response leaving content consumers vulnerable to attack if they dont handle the data properly. The fixing process of this error was a little more complex. It included:
    - Using a vetted library of a framework that generate properly encoded output
    - Ensuring that client-side and server-side have the same security checks by using different encoding methods
    - Setting session cookies
    - Ensuring input validation

(Informal):
Authentication Request Identified - amount: 1
- This response informed that a request was identified as an authentication request. According to the ZAP report, this was more of an alert rather than a vulnerability.

Information Disclosure - Suspicious Comments - amount: 1
- This response contained comments which could help an attacker. The solution would be to remove those comments.

Loosely Scoped Cookie - amount: 2
- This response stated how cookies can be scoped by a parent domain or a subdomain. If a cookie is scoped by a parent domain, all subdomains of that parent domain can access the cookie. The solution is to always scope cookies to FQDN (Fully Qualified Domain Name).

Modern Web Application - amount: 1
- This response simply stated that the used application was a modern web application. This one was also an informal alert, so there was nothing to fix.

Session Management Response Identified - amount: 2
- This response was again an informal alert. It said that the response itself contains a session management token.

User Agent Fuzzer - amount: 108
- This response checks for differences in the mobile sites and compares the statuscode and hashcode of the response body. This response didn't have a solution, likely because it is a simple test for the previously mentioned codes.
