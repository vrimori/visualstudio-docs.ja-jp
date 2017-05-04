---
title: "add メソッド (Set) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# add メソッド (Set) (JavaScript)
セットに新しい要素を追加します。  
  
## 構文  
  
```javascript  
setObj.add(value)  
```  
  
#### パラメーター  
 `setObj`  
 必須です。  `Set` オブジェクト。  
  
 `value`  
 必須です。  `Set` の新しい要素を指定します。  
  
## 解説  
 新しい要素は、任意の型で、一意である必要があります。  `Set` に一意でない要素を追加する場合、新しい要素はコレクションに追加されません。  
  
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