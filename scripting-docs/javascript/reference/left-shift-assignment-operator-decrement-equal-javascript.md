---
title: "左シフト代入演算子 (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<= 演算子 [JavaScript]"
  - "左シフト代入演算子 (<<=) [JavaScript]"
  - "左シフト演算子 [JavaScript]"
  - "代入演算子、JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 左シフト代入演算子 (&lt;&lt;=) (JavaScript)
指定したビット数を左へ移動し、`result` に結果を代入します。  演算によって空いたビットは 0 で埋められます。  
  
## 構文  
  
```  
  
result <<= expression  
```  
  
## パラメーター  
 `result`  
 任意の変数を指定します。  
  
 `expression`  
 移動するビットの数。  
  
## 解説  
 `<<=` 演算子を使用することは、`result = result << expression` を使用することと同じです。  
  
 `<<=` 演算子を使用する方法の例を次に示します。  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの左シフト演算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [ビットごとの右シフト演算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [符号なし右シフト演算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)