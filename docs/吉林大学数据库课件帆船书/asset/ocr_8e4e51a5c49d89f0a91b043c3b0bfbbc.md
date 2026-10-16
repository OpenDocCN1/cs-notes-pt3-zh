# Digital Certificates

+   - **Digital certificates** are used to verify authenticity of public keys.
+   - Problem: when you communicate with a web site, how do you know if you are talking with the genuine web site or an imposter?
+     - Solution: use the public key of the web site
+     - Problem: how to verify if the public key itself is genuine?
+   - Solution:
+     - Every client (e.g., browser) has public keys of a few root-level **certification authorities**
+     - A site can get its name/URL and public key signed by a certification authority: signed document is called a **certificate**
+     - Client can use public key of certification authority to verify certificate
+     - Multiple levels of certification authorities can exist. Each certification authority
+       - presents its own public-key certificate signed by a higher level authority, and
+       - uses its private key to sign the certificate of other web sites/authorities