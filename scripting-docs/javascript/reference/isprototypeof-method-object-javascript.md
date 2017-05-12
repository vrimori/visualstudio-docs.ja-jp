---
title: "isPrototypeOf メソッド (Object) (JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf メソッド"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# isPrototypeOf メソッド (Object) (JavaScript)
オブジェクトが別のオブジェクトのプロトタイプ チェーンに存在するかどうかを判定します。  
  
## 構文  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## パラメーター  
 `prototype`  
 必須。  オブジェクトのプロトタイプ。  
  
 `object`  
 必須。  プロトタイプ チェーンをチェックする別のオブジェクト。  
  
## 解説  
 `object` のプロトタイプ チェーンに `prototype` がある場合、`isPrototypeOf` メソッドは `true` を返します。  プロトタイプ チェインは、同じオブジェクト型のインスタンス間で機能を共有するときに使用します。  `object` がオブジェクトではない場合、または `prototype` が `object` のプロトタイプ チェーンに存在しない場合、`isPrototypeOf` メソッドは `false` を返します。  
  
## 使用例  
 `isPrototypeOf` メソッドの使用例を次に示します。  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [prototype プロパティ \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)