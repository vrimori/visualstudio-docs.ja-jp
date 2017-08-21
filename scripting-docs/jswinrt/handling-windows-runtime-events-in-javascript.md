---
title: "JavaScript での Windows ランタイム イベントの処理 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="handling-windows-runtime-events-in-javascript"></a>JavaScript での Windows ランタイム イベントの処理
JavaScript での Windows ランタイム イベントは、C++ や .NET Framework とは異なる方法で表現されます。 これらのイベントは、クラス プロパティではなく、クラスの `addEventListener` および `removeEventListener` メソッドに渡される文字列識別子として表現されます。 たとえば、`Geolocator.addEventListener` メソッドに "positionchanged" という文字列を渡すことで、[Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) イベントのイベント ハンドラーを追加できます。  
  
```JavaScript  
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
  
 Windows ランタイム イベント引数は、JavaScript では単一のイベント オブジェクトとして表現されます。 以下のイベント ハンドラー メソッドの例では、`ev` パラメーターは、送信元 (ターゲット プロパティ) とその他のイベント引数の両方を格納するオブジェクトです。 イベント引数とは、各イベントについてドキュメント化される引数のことです。  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## <a name="see-also"></a>関連項目  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)
