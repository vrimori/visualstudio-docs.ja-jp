---
title: このステートメント (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640322"
---
# <a name="this-statement-javascript"></a>this ステートメント (JavaScript)
現在のオブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
this.property  
```  
  
## <a name="remarks"></a>コメント  
 必須の `property` 引数は、現在のオブジェクトのいずれかのプロパティです。  
  
 キーワード `this` は、オブジェクト コンストラクターで現在のオブジェクトを参照するために使用できます。  
  
## <a name="example"></a>例  
 次の例では、**この**新しく作成された Car オブジェクトを参照し、3 つのプロパティに値を割り当てます。  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 **この**キーワードは通常、参照、**ウィンドウ**オブジェクトの場合、その他のオブジェクトのスコープ外で使用します。 ただし、イベント ハンドラー内では、`this` はイベントを発生させた DOM 要素を示します。  
  
 (Internet Explorer 9 以降用の) 次のコードでは、イベント ハンドラーは、ID が "clicker" のボタンの文字列バージョンを出力します。  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [bind メソッドの使用](../../javascript/advanced/using-the-bind-method-javascript.md)