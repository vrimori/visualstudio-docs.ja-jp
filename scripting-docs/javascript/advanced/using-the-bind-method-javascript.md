---
title: bind メソッドの使用 (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d185801cc5bba355751147edb79b9c47d21f8eed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987868"
---
# <a name="using-the-bind-method-javascript"></a>bind メソッドの使用 (JavaScript)
JavaScript の `bind` メソッドには複数の用途があります。 通常は、別のコンテキストで実行される関数の実行コンテキストを保持するために使用されます。 `bind` は、元の関数と同じ本体を持つ、新しい関数を作成します。 `bind` に渡される最初の引数で、バインドされた関数の `this` キーワードの値が指定されます。 また、`bind` への省略可能な追加の引数を渡すこともできます。 その他の用途の例については、「[bind メソッド (Function)](../../javascript/reference/bind-method-function-javascript.md)」をご覧ください。 部分的に関数を適用する `bind` の使用例については、「[Hilo での非同期プログラミング パターンとヒント (JavaScript と HTML を使った Windows ストア アプリ)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx)」をご覧ください。  
  
## <a name="preserving-the-execution-context-using-bind"></a>バインドを使用した実行コンテキストの保持  
 `bind` 関数は、イベント リスナーを追加する場合によく使用されます。 次のコード例では、`bind` を使用して、現在のオブジェクト (`DataObject`) のコンテキストを保持しています。 データ オブジェクトは、`bind` キーワードを使用して `this` に渡されます。このキーワードで、イベント ハンドラー (`dataReadyHandler`) の実行時にデータ オブジェクトのプロパティや関数にアクセスできます。 `bind` が機能するしくみを説明するために、このコードではカスタム イベントを作成します。  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 `bind` を使用するコード行をコメント アウトし、`addEventListener` なしで `bind` を呼び出すコード行のコメントを解除してから、コードを再実行すると、`dataReadyHandler` 関数は失敗します。 たとえば、`dataReadyHandler` では、`this.name` が未定義になります。また、`this.data()` オブジェクトがデータ オブジェクトを参照しなくなるため、`this` がエラーになります。  
  
## <a name="see-also"></a>参照  
 [bind メソッド (Function)](../../javascript/reference/bind-method-function-javascript.md)
