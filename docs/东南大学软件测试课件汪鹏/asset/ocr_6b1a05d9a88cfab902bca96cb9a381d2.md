# LoadRunner——部署和安装

```
vuser_init()
{
    lr_start_transaction("login");
    web_url("MercuryWebTours",
        "URL=http://localhost/MercuryWebTours/",
        "Resource=0",
        "RecContentType=text/html",
        "Referer=",
        "Snapshot=t6.inf",
        "Mode=HTML",
        LAST);

```

Vuser Terminated.