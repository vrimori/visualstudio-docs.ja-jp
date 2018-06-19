---
title: イベント リスナーの管理 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569222"
---
# <a name="managing-event-listeners"></a>イベント リスナーの管理
DOM 要素またはオブジェクトの有効期間が対応するイベント リスナーの有効期間と異なる場合には、メモリ リークを回避するために、[removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx) メソッドを使用しなければならないこともあります。  
  
## <a name="event-listeners-and-object-scope"></a>イベント リスナーとオブジェクト スコープ  
 次のコード例は、`dataObjFactory()` 関数が呼び出された際にメモリー リークにつながる可能性のあるコードを示します。 このコードでは、新しいデータ オブジェクトが作成されるたびに、データ オブジェクトのイベント リスナーが登録されます。 現在のデータ オブジェクトを `dataReady()` イベント ハンドラーで利用できるようにするには、[bind メソッド (Function)](../../javascript/reference/bind-method-function-javascript.md) を `addEventListener` で使います。  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 各データ オブジェクトのリスナーが `document` オブジェクトで登録されます。このオブジェクトの有効期間は、データ オブジェクトとは異なります。 各データ オブジェクトの登録されたイベント リスナーは、`document` オブジェクトがスコープ内に残っている限り、そのデータ オブジェクトがガベージ コレクションされないようにします。 (一部のモダンな JavaScript デザイン パターンでは、ドキュメント オブジェクトは Web アプリの有効期間にわたってスコープ内に残ります。)メモリ リークを防止するために、`removeEventListener` は `dataObjFactory` 関数で呼び出します。 ただしこのコードは、`bind` 関数が返したイベント ハンドラーのバインド バージョンでは `removeEventListener` が呼び出されていないため失敗します。  
  
 このコードを修正してデータ オブジェクトをガベージ コレクションで利用できるようにするには、次のコードに示すように、まずイベント ハンドラーのバウンド バージョンへの参照を保存する必要があります。その後、保存した参照を `addEventListener` へ渡します。 次に、`DataObject` の修正コードを示します。  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 最後に、バインドされた関数の保存された参照 (`removeEventListener`) 上で `handlerRef` を呼び出す必要があります。 次に、`dataObjFactory` の修正コードを示します。  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 これで `removeEventListener` への呼び出しが機能して、`document` オブジェクトがスコープ内にある場合でも不必要なデータ オブジェクトをガベージ コレクションすることが可能です。