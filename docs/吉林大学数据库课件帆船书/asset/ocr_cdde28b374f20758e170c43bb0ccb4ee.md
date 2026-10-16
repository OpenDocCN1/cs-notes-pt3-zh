# PASSWORD LEAKAGE

+   - Never store passwords, such as database passwords, in clear text in scripts that may be accessible to users
+     - E.g. in files in a directory accessible to a web server
+       - Normally, web server will execute, but not provide source of script files such as file.jsp or file.php, but source of editor backup files such as file.jsp~ or .file.jsp.swp may be served

+   - Restrict access to database server from IPs of machines running application servers
+     - Most databases allow restriction of access by source IP address