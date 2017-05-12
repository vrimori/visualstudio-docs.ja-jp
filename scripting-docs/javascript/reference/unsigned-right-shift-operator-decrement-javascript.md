---
title: "符号なし右シフト演算子 (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> 演算子"
  - "符号なし右シフト演算子 (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 符号なし右シフト演算子 (&gt;&gt;&gt;) (JavaScript)
式の各ビットを指定されたビット数分だけ右へシフトします。ただし、符号は保持されません。  
  
## 構文  
  
```  
  
result = expression1 >>> expression2  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression1*  
 任意の式を指定します。  
  
 *expression2*  
 任意の式を指定します。  
  
## 解説  
 **\>\>\>** 演算子は、*expression1* の各ビットを *expression2* で指定されたビット数分だけ右へシフトします。  上位ビットは、0 で埋められます。  シフトされて最下位ビットより右へ移動した桁は破棄されます。  次に例を示します。  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 変数 *temp* の初期値は、\-14 \(2 の補数バイナリで 11111111 11111111 11111111 11110010\) です。  右に 2 ビット分シフトすると、値は 1073741820 \(2 進数で 00111111 11111111 11111111 11111100\) になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [符号なし右シフト代入演算子 \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [ビットごとの左シフト演算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [ビットごとの右シフト演算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)