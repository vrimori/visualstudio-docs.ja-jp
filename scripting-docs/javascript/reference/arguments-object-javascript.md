---
title: "arguments オブジェクト (JavaScript) | Microsoft Docs"
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
  - "arguments オブジェクト"
  - "引数, arguments オブジェクト"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# arguments オブジェクト (JavaScript)
現在実行中の関数の引数、およびその呼び出し元の関数を表すオブジェクトです。  
  
## 構文  
  
```  
[function.]arguments[n]  
```  
  
## Parameters  
 *機能性*  
 Optional.  現在実行中の `Function` オブジェクトの名前を指定します。  
  
 *n*  
 Required.  `Function` オブジェクトに渡される引数値の 0 から始まるインデックスを指定します。  
  
## 解説  
 **arguments** オブジェクトを明示的に作成することはできません。  **arguments** オブジェクトは、関数の実行が開始されたときにのみ使用できるようになります。  関数の **arguments** オブジェクトは配列ではありませんが、配列の各要素にアクセスする場合と同じ方法で各引数にアクセスできます。  インデックス *n* は、実際には **arguments** オブジェクトの **0** ***n*** のプロパティの 1 つに対する参照です。  
  
## 使用例  
 次のコードは、**arguments** オブジェクトの使用例です。  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [0...n プロパティ \(arguments\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee プロパティ \(arguments\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length プロパティ \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)