```
/* 例2-12.css */
ul{  width:360px;
    padding:0;
    margin:0 auto;
    list-style:none;}
li{  float:left;
    width:120px;
    background-color:#eee;}
ul li a{
    display:block;
    font-family:"微软雅黑","宋体";
    font-size:12px;
    border:1px solid #000;
    padding:3px;
    text-decoration:none;
    text-align:center;
    color:#777;}
ul li a:hover{
    background-color:#fff;
    color:#000;}
li ul{
    width:120px;
    display:none;}
li:hover ul{
    display:block;}
ul li ul li a{
    border:1px solid #fff;
    color:#fff;
    background-color:#e12e6b;}
ul li ul li a:hover{
    background-color:#fff;
    color:#e12e6b;}
```