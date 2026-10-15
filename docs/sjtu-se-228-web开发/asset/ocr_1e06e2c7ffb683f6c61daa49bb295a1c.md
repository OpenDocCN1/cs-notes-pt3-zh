+   - Append the followings to `conf/httpd.conf`

```
PHPIniDir "E:/php-5.5.8/"
LoadModule php5_module "E:/php-5.5.8/php5apache2_4.dll"
AddType application/x-httpd-php .php
```

+   - where,
+     - PHPIniDir is the directory of PHP home.
+     - LoadModule is in the directory of PHP home, which allows the support to PHP is loaded as a module of Apache HTTP Server.