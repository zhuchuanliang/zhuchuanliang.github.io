---
layout: wiki
title: ����ʱС����
categories: tools
description: JSP�ĵ���ʱС����
keywords: JSP
---

## Դ���� ##

    <!doctype html public "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <head>
    <title> ����ʱЧ�� </title>
    <script language="JavaScript">
    
    var startTime = new Date();//�����new Date()�������̨���ݵ�ʱ��
    var EndTime=startTime.getTime()+20*60*1000;//������õ���ʱ��ʱ�䣬�������㣬Ҳ��60*1000����һ����
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
    alert("�����������ӣ�");
    }
    setTimeout("GetRTime()",1000);
    }
    window.onload=GetRTime;
    
    </script>
    </head>
    <body>
    <div id="CountMsg">����ʱ���У�<strong id="RemainD"></strong><strong id="RemainH">XX</strong>ʱ<strong id="RemainM">XX</strong>��<strong id="RemainS">XX</strong>��</div>
    </body>
    </html>  
## Ч��Ԥ��
[����ʱ����](F:\Github\zhuchuanliang.github.io\tools\����ʱ.html "����ʱ����")    