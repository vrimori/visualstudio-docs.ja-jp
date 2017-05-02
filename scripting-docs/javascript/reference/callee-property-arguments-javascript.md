---
title: "callee プロパティ (arguments) (JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee プロパティ"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# callee プロパティ (arguments) (JavaScript)
指定した `Function` オブジェクトの本体である実行中の `Function` オブジェクトを返します。  
  
## 構文  
  
```  
[function.]arguments.callee  
```  
  
## 解説  
 省略可能な *function* 引数は、の現在実行中の `Function` オブジェクトの名前です。  
  
 `callee` プロパティは **arguments** オブジェクトのメンバーで、対応する関数が実行されている場合のみ使用できます。  
  
 `callee` プロパティの初期値は、実行中の `Function` オブジェクトになります。  これにより、無名関数を再帰的に使用できます。  
  
## 使用例  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [arguments オブジェクト](../../javascript/reference/arguments-object-javascript.md)&#124; [Function オブジェクト](../../javascript/reference/function-object-javascript.md)  
  
## 参照  
 [caller プロパティ \(Function\)](../../javascript/reference/caller-property-function-javascript.md)