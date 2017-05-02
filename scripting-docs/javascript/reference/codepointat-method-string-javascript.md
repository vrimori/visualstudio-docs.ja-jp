---
title: "codePointAt メソッド (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# codePointAt メソッド (String) (JavaScript)
Unicode UTF\-16 文字のコード ポイントを返します。  
  
## 構文  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### パラメーター  
 `stringObj`  
 必須。  String オブジェクト。  
  
 `pos`  
 必須。  文字の位置。  
  
## 解説  
 このメソッドは、すべての UTF\-16 文字のコード ポイント値を返します。アストラル コード ポイント \(16 進数字 4 桁を超えるコード ポイント\) も含みます。  
  
 `pos` がゼロ \(0\) 未満か文字列のサイズを超える場合、戻り値は `undefined` です。  
  
## 使用例  
 `codePointAt` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]