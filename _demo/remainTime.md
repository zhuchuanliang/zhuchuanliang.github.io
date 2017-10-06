---
layout: wiki
title: 倒计时小程序
categories: tools
description: JSP倒计时小程序
keywords: JSP
---

## 源码  

   ```javascript
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
```
    
    
	


    
    
    
    
	
## 效果预览
[倒计时程序](https://zhuchuanliang.github.io/demo/倒计时.html "倒计时程序")