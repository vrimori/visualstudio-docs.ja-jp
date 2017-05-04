---
title: "条件 (三項) 演算子 (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "条件 (三項) 演算子"
  - "条件演算子"
  - "三項"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 条件 (三項) 演算子 (?:) (JavaScript)
条件に応じて 2 つの式のどちらかを返します。  
  
## 構文  
  
```  
  
test ? expression1 : expression2  
```  
  
## パラメーター  
 `test`  
 任意のブール式。  
  
 `expression1`  
 `test` が `true` の場合は式が返されます。  コンマ式も使用できます。  
  
 `expression2`  
 `test` が `false` の場合は式が返されます。  複数の式がコンマ式によってリンクされている可能性があります。  
  
## 解説  
 `?:` 演算子を使用して、`if...else` ステートメントと同じ処理を簡単に実行できます。  この演算子は通常、`if...else` ステートメントが記述しづらい長い式の 1 部として使用されます。  次に例を示します。  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 この例は、午後 6 時以降の場合 "Good evening." という文字列を作成します。  上記の例は、`if...else` ステートメントを使用すると、次のようになります。  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [if...else ステートメント](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Script Junkie 構成ウィジェットのサンプル アプリ](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)