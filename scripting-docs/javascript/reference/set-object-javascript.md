---
title: "Set オブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Set オブジェクト (JavaScript)
任意の型の、一意の値のコレクションです。  
  
## <a name="syntax"></a>構文  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>コメント  
 `Set` に一意でない値を追加しようとすると、新しい値はコレクションに追加されません。  
  
## <a name="properties"></a>プロパティ  
 `Set` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[コンス トラクター](../../javascript/reference/constructor-property-set.md)|セットを作成する関数を指定します。|  
|[プロトタイプ](../../javascript/reference/prototype-property-set.md)|セットのプロトタイプへの参照を返します。|  
|[size](../../javascript/reference/size-property-set-javascript.md)|セット内の要素数を返します。|  
  
## <a name="methods"></a>メソッド  
 `Set` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|セットに要素を追加します。|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|セットからすべての要素を削除します。|  
|[削除](../../javascript/reference/delete-method-set-javascript.md)|指定された要素をセットから削除します。|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|セットの各要素に対して、指定された処理を実行します。|  
|[が](../../javascript/reference/has-method-set-javascript.md)|セットが指定した要素を格納している場合、`true` を返します。|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|セットの文字列表現を返します。|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## <a name="example"></a>例  
 次の例は、メンバーをセットに追加して取得する方法を示します。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]