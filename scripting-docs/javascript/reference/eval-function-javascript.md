---
title: "eval 関数 (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval 関数"
  - "解析、コード"
  - "パーサー"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# eval 関数 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードを評価し、実行します。  
  
## 構文  
  
```  
eval(codeString)   
```  
  
## パラメーター  
 `codeString`  
 必須です。  有効な [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードを含む `String` を指定します。  
  
## 解説  
 `eval` 関数を使用すると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ソース コードを動的に実行できます。  
  
 `codeString` 文字列は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] パーサーによって解析され、実行されます。  
  
 `eval` 関数に渡されるコードは、`eval` 関数を呼び出した場合と同じように実行されます。  
  
 JSON （JavaScript Object Notation） テキストの逆シリアル化には、できるだけ [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)を使用します。  `JSON.parse` 関数は、`eval` 関数より高速で安全に実行されます。  
  
## 使用例  
 次のコードでは、`myDate` 変数がテスト用の日付に初期化されます。  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 参照  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)