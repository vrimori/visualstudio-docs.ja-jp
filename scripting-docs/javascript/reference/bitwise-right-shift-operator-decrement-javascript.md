---
title: "ビットごとの右シフト演算子 (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> 演算子"
  - ">> 演算子, 概要 (>> 演算子の)"
  - ">> 演算子, ビットセット"
  - "ビット処理演算子, 右シフト演算子"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# ビットごとの右シフト演算子 (&gt;&gt;) (JavaScript)
式の各ビットを指定されたビット数分だけ右へシフトします。ただし、符号は保持されます。  
  
## 構文  
  
```  
  
result = expression1 >> expression2  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression1*  
 任意の式を指定します。  
  
 *expression2*  
 任意の式を指定します。  
  
## 解説  
 \>\> 演算子は、*expression1* の各ビットを *expression2* で指定されたビット数分だけ右へシフトします。  上位ビットは、*expression1* の符号ビットで埋められます。  シフトされて最下位ビットより右へ移動した桁は破棄されます。  たとえば次に示すコードでは、変数 *temp* の値は、\-14 \(2 の補数バイナリで 11110010\) から 2 ビット分だけ右へシフトされて \-4 \(2 の補数バイナリで 11111100\) になります。  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの左シフト演算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [右シフト代入演算子 \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [符号なし右シフト演算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)