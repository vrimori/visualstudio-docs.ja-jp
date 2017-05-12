---
title: "JavaScript での Windows ランタイム イベントの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows ランタイム イベント"
  - "Windows ランタイム イベント [JavaScript]"
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JavaScript での Windows ランタイム イベントの処理
JavaScript での Windows ランタイム イベントは、C\+\+ や .NET Framework とは異なる方法で表現されます。  これらのイベントは、クラス プロパティではなく、クラスの `addEventListener` および `removeEventListener` メソッドに渡される文字列識別子として表現されます。  例えば、[Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) イベントのイベント ハンドラーを追加するには、文字列 "positionchanged" を `Geolocator.addEventListener` メソッドに渡します。  
  
```javascript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 `locator.onpositionchanged` プロパティを設定することもできます。  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 Windows ランタイム イベント引数は、JavaScript では単一のイベント オブジェクトとして表現されます。  以下のイベント ハンドラー メソッドの例では、`ev` パラメーターは、送信元 \(ターゲット プロパティ\) とその他のイベント引数の両方を格納するオブジェクトです。  イベント引数とは、各イベントについてドキュメント化される引数のことです。  
  
```javascript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## 参照  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)