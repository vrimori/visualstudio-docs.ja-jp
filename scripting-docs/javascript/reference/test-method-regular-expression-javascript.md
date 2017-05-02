---
title: "test メソッド (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "テスト メソッド"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# test メソッド (Regular Expression) (JavaScript)
文字列内で検索パターンに一致する部分が存在するかどうかを調べ、結果を示すブール値を返します。  
  
## 構文  
  
```  
  
rgExp.test(str)   
```  
  
## パラメーター  
 `rgExp`  
 必須です。  検索に使用する正規表現のパターンと適用できるフラグを格納した **Regular Expression** オブジェクトのインスタンスです。  
  
 `str`  
 必須です。  検索対象となる文字列を指定します。  
  
## 解説  
 **test** メソッドは、文字列内にパターンに一致する部分が存在するかどうかをチェックして、存在する場合は **true** を返し、存在しない場合は **false** を返します。  
  
 グローバルの `RegExp` オブジェクトのプロパティは **test** メソッドでは変更されません。  
  
## 使用例  
 **test** メソッドの使用例を次に示します。  この例を使用するには、正規表現パターンおよび文字列に関数を渡します。  関数は、文字列内に正規表現パターンに一致する部分が存在するかどうかをテストし、検索結果を示す文字列を返します。  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 参照  
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)