# An Example

+   - The following is a typical sequence of events:
+     1. A client (e.g., a Web browser) accesses a Web server and makes an HTTP request.
+     2. The request is received by the Web server and handed off to the servlet container.
+        - The servlet container can be running in the same process as the host Web server, in a different process on the same host, or on a different host from the Web server for which it processes requests.
+     3. The servlet container determines which servlet to invoke based on the configuration of its servlets, and calls it with objects representing the request and response.
+     4. The servlet uses the request object to find out who the remote user is, what HTTP POST parameters may have been sent as part of this request, and other relevant data.
+        - The servlet performs whatever logic it was programmed with, and generates data to send back to the client. It sends this data back to the client via the response object.
+     5. Once the servlet has finished processing the request, the servlet container ensures that the response is properly flushed, and returns control back to the host Web server.