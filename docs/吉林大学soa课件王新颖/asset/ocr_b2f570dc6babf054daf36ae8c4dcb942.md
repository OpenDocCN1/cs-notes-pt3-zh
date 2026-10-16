```
```xml
<SOAP-ENV:Envelope
    xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
    SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
    <SOAP-ENV:Header>
        <t:Trans xmlns:t="http://www.w3school.com.cn/transaction/"
                 SOAP-ENV:mustUnderstand="1">5</t:Trans>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <m:GetLastTradePrice xmlns:m="Some-URI">
            <symbol>DEF</symbol>
        </m:GetLastTradePrice>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
```

> From the: Simple Object Access Protocol (SOAP) 1.1 W3C Note 08 May 2000