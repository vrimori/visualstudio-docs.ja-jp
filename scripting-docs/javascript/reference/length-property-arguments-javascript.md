---
title: "length プロパティ (arguments) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length プロパティ"
  - "length プロパティ (arguments)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# length プロパティ (arguments) (JavaScript)
関数を呼び出すときに実際に渡された引数の数を返します。  
  
## 構文  
  
```  
[function.]arguments.length  
```  
  
## 解説  
 省略可能な *function* 引数は、の現在実行中の `Function` オブジェクトの名前です。  
  
 **arguments** オブジェクトの **length** プロパティは、スクリプト エンジンによって、関数が実行されるときに `Function` オブジェクトに渡される引数の実際の数に初期化されます。  
  
## 使用例  
 **arguments** オブジェクトの **length** プロパティの使用例を次に示します。  この例を十分に理解するために、関数で必要とされる数 \(2 つ\) より多い引数を渡します。  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [arguments オブジェクト](../../javascript/reference/arguments-object-javascript.md)&#124; [Function オブジェクト](../../javascript/reference/function-object-javascript.md)  
  
## 参照  
 [arguments プロパティ \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length プロパティ \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [length プロパティ \(String\)](../../javascript/reference/length-property-string-javascript.md)