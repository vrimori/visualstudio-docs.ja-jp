---
title: "in 演算子 (JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in 演算子"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# in 演算子 (JavaScript)
オブジェクトにプロパティがあるかどうかを調べます。  
  
## 構文  
  
```  
  
result = property in object  
```  
  
## パラメーター  
 `result`  
 必須です。  任意の変数を指定します。  
  
 `property`  
 必須です。  文字列型に評価される式を指定します。  
  
 `object`  
 必須です。  任意のオブジェクトを指定します。  
  
## 解説  
 `in` 演算子は、オブジェクトに `property` という名前のプロパティがあるかどうかを調べます。  また、プロパティがオブジェクトのプロトタイプ チェーンの一部かどうかを判定します。  オブジェクト プロトタイプの詳細については、「[プロトタイプとプロトタイプ継承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)」を参照してください。  
  
## 使用例  
 `in` 演算子を使用する方法の例を次に示します。  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)