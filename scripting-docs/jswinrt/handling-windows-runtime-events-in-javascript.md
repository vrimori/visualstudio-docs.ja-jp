---
title: JavaScript での Windows ランタイム イベントの処理 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302812"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>JavaScript での Windows ランタイム イベントの処理
JavaScript での Windows ランタイム イベントは、C++ や .NET Framework とは異なる方法で表現されます。 これらのイベントは、クラス プロパティではなく、クラスの `addEventListener` および `removeEventListener` メソッドに渡される (小文字の) 文字列識別子として表現されます。 たとえば、`Geolocator.addEventListener` メソッドに "positionchanged" という文字列を渡すことで、[Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) イベントのイベント ハンドラーを追加できます。  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 `locator.onpositionchanged` プロパティを設定することもできます。  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
.NET/C++ と JavaScript のもう 1 つの違いは、イベント ハンドラーによって取得されるパラメーターの数です。 .NET/C++ の場合、ハンドラーはパラメーターを 2 つ取得します。イベント送信元とイベント データです。 JavaScript の場合、2 つのパラメーターは 1 つの `Event` オブジェクトとしてバンドルされます。 次の例では、`ev` パラメーターにイベントの送信元 (`target` プロパティ) とイベント データ プロパティ (ここでは、`position`) の両方が含まれています。 イベント データ プロパティとは、各イベントについてドキュメント化される引数のことです。
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## <a name="see-also"></a>参照  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)
