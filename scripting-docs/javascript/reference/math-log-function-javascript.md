---
title: "Math.log 関数 (JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log メソッド"
  - "Math オブジェクト"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Math.log 関数 (JavaScript)
数値の自然対数 \(底 `e`\) を返します。  
  
## 構文  
  
```  
Math.log(number)   
```  
  
#### パラメーター  
 number  
 数値。  
  
## 戻り値  
 `number` が正の場合、この関数はこの数値の自然対数を返します。  `number` が負の場合、この関数は `NaN` を返します。  `number` が 0 の場合、この関数は `-Infinity` を返します。  
  
## 使用例  
 この関数の使用方法を次のコード例に示します。  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 参照  
 [Math.sqrt 関数](../../javascript/reference/math-sqrt-function-javascript.md)