---
layout: wiki
title: 倒计时小程序
categories: tools
description: JSP倒计时小程序
keywords: JSP
---

## 源码  

   ```
    <html>
    <!doctype html public "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <head>
    <title> 倒计时效果 </title>
    <script language="JavaScript">
    var startTime = new Date();
    var EndTime=startTime.getTime()+20*60*1000;
    function GetRTime(){
    var NowTime = new Date();
    var nMS =EndTime - NowTime.getTime();
    var nH=Math.floor(nMS/(1000*60*60)) % 24;
    var nM=Math.floor(nMS/(1000*60)) % 60;
    var nS=Math.floor(nMS/1000) % 60;
     document.getElementById("RemainH").innerHTML=nH;
     document.getElementById("RemainM").innerHTML=nM;
     document.getElementById("RemainS").innerHTML=nS;
    if(nMS>5*59*1000&&nMS<=5*60*1000)
    {
    alert("还有最后五分钟！");
    }
    setTimeout("GetRTime()",1000);
    }
    window.onload=GetRTime;
    
    </script>
    </head>
    <body>
    <div id="CountMsg">倒计时还有：<strong id="RemainD"></strong><strong id="RemainH">XX</strong>时<strong id="RemainM">XX</strong>分<strong id="RemainS">XX</strong>秒</div>
    </body>
    </html>
    
    ```
    
    
	


    
    
    
    
	
## 效果预览
[倒计时程序](https://zhuchuanliang.github.io/tools/1.html "倒计时程序")