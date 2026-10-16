# CROSS SITE SCRIPTING

+   HTML code on one page executes action on another page
+   - E.g. <img src = http://mybank.com/transfermoney?amount=1000&toaccount=14523>
+   - Risk: if user viewing page with above code is currently logged into mybank, the transfer may succeed
+   - Above example simplistic, since GET method is normally not used for updates, but if the code were instead a script, it could execute POST methods

Above vulnerability called cross-site scripting (XSS) or cross-site request forgery (XSRF or CSRF)

+   Prevent your web site from being used to launch XSS or XSRF attacks
+   - Disallow HTML tags in text input provided by users, using functions to detect and strip such tags

+   Protect your web site from XSS/XSRF attacks launched from other sites
+   - ..next slide