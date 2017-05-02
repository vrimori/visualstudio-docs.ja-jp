---
title: "Math.acosh 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.acosh 関数 (JavaScript)
数値のハイパーボリック アークコサイン \(または逆ハイパーボリック コサイン\) を返します。  
  
## 構文  
  
```  
Math.acosh(number)  
```  
  
#### パラメーター  
 必要な `number` 引数は、数値式です。  
  
## 戻り値  
 `number` 引数の逆ハイパーボリック コサインをラジアンで返します。  
  
## 使用例  
 次のコードは、`acosh` 関数の使用方法を示しています。  
  
```javascript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## 解説  
 **対象**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 参照  
 [Math.acos 関数](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin 関数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 関数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 関数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 関数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 関数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)