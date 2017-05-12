---
title: "ビットごとの左シフト演算子 (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< 演算子"
  - "<< 演算子, << 演算子の概要"
  - "ビット処理演算子, 左シフト演算子"
  - "左シフト演算子"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# ビットごとの左シフト演算子 (&lt;&lt;) (JavaScript)
式の各ビットを指定されたビット数分だけ左へシフトします。  
  
## 構文  
  
```  
  
result = expression1 << expression2  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression1*  
 任意の式を指定します。  
  
 *expression2*  
 任意の式を指定します。  
  
## 解説  
 **\<\<** 演算子は、*expression1* の各ビットを *expression2* で指定されたビット数分だけ左へシフトします。  次に例を示します。  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 変数 *temp* の値は、14 \(2 進数の 00001110\) から 2 ビット分だけ左シフトされて 56 \(2 進数の 00111000\) になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [左シフト代入演算子 \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [ビットごとの右シフト演算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [符号なし右シフト演算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)