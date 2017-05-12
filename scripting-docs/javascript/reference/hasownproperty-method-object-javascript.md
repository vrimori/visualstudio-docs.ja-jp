---
title: "hasOwnProperty メソッド (Object) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty メソッド"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# hasOwnProperty メソッド (Object) (JavaScript)
指定された名前のプロパティがオブジェクトにあるかどうかを確認します。  
  
## 構文  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## パラメーター  
 `object`  
 必須です。  オブジェクトのインスタンスを指定します。  
  
 `proName`  
 必須です。  プロパティ名の文字列値を指定します。  
  
## 解説  
 指定した名前のプロパティが `object` にある場合、`hasOwnProperty` メソッドは `true` を返し、プロパティがない場合は `false` を返します。  このメソッドは、オブジェクトのプロトタイプ チェインにあるプロパティをチェックしません。プロパティはオブジェクト自身のメンバーである必要があります。  
  
 このプロパティは、Internet Explorer 8 およびそれ以前のホスト オブジェクトではサポートされません。  
  
## 使用例  
 すべての `String` オブジェクトが共通メソッド split を共有している場合の例を次に示します。  次のコードは **false** と **true** を表示します。  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [in 演算子](../../javascript/reference/in-operator-decrementjavascript.md)