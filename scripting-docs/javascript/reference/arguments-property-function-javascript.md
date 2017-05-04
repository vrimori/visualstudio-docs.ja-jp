---
title: "arguments プロパティ (Function) (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments、arguments プロパティ"
  - "Arguments プロパティ"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# arguments プロパティ (Function) (JavaScript)
現在実行中の `Function` オブジェクトの引数を取得します。  
  
## 構文  
  
```  
  
function.arguments  
```  
  
## 解説  
 `function` 引数は、現在実行中の関数の名前で、省略可能です。  
  
 このプロパティを使用すると、1 つの関数が可変個の引数を処理できます。  `arguments` オブジェクトの **length** プロパティには、関数に渡された引数の数が設定されています。  `arguments` オブジェクトの各引数には、各引数は、配列要素にアクセスするのと同じ方法でアクセスできます。  
  
## 使用例  
 `arguments` プロパティの使用例を次に示します。  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [arguments オブジェクト](../../javascript/reference/arguments-object-javascript.md)   
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)