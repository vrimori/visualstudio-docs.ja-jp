---
title: "Set オブジェクト (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Set オブジェクト (JavaScript)
任意の型の、一意の値のコレクションです。  
  
## 構文  
  
```  
setObj = new Set()  
  
```  
  
## 解説  
 `Set` に一意でない値を追加しようとすると、新しい値はコレクションに追加されません。  
  
## プロパティ  
 `Set` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[コンストラクター](../../javascript/reference/constructor-property-set.md)|セットを作成する関数を指定します。|  
|[prototype](../../javascript/reference/prototype-property-set.md)|セットのプロトタイプへの参照を返します。|  
|[size](../../javascript/reference/size-property-set-javascript.md)|セット内の要素数を返します。|  
  
## メソッド  
 `Set` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|セットに要素を追加します。|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|セットからすべての要素を削除します。|  
|[delete](../../javascript/reference/delete-method-set-javascript.md)|指定された要素をセットから削除します。|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|セットの各要素に対して、指定された処理を実行します。|  
|[has](../../javascript/reference/has-method-set-javascript.md)|セットが指定した要素を格納している場合、`true` を返します。|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|セットの文字列表現を返します。|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## 使用例  
 次の例は、メンバーをセットに追加して取得する方法を示します。  
  
```javascript  
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
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]