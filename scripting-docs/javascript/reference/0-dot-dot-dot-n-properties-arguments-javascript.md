---
title: "0...n プロパティ (arguments) (JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "0...n プロパティ"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 0...n プロパティ (arguments) (JavaScript)
実行した関数の **arguments** プロパティで返される **arguments** オブジェクトから、各引数の実際の値を返します。  
  
## 構文  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## パラメーター  
 *function*  
 省略可能です。  現在実行中の `Function` オブジェクトの名前を指定します。  
  
 0, 1, 2, *, n*  
 必須です。  0 ～ *n* の範囲で負ではない整数を指定します。0 は 1 番目の引数を表し、*n* は最後の引数を表します。  最後の引数 *n* の値は **arguments.length\-1** です。  
  
## 解説  
 0 ～   .  .  n の各プロパティが返す値は、実行している関数に渡す実際の値です。  **arguments** オブジェクトは引数の配列ではありませんが、それを構成する各引数には、配列要素にアクセスする方法と同じ方法でアクセスされます。  
  
## 使用例  
 次の例は、**..arguments** オブジェクトの **0** ～ ***n*** の各プロパティを使用しています。  この例を十分に理解するために、1 つ以上の引数を関数に渡します。  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [arguments オブジェクト](../../javascript/reference/arguments-object-javascript.md)&#124; [Function オブジェクト](../../javascript/reference/function-object-javascript.md)  
  
## 参照  
 [length プロパティ \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length プロパティ \(Function\)](../../javascript/reference/length-property-function-javascript.md)