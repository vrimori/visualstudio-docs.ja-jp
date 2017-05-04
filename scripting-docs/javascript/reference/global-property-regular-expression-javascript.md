---
title: "global プロパティ (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global プロパティ"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# global プロパティ (Regular Expression) (JavaScript)
正規表現で使用する global フラグ \(**g**\) の状態を表すブール値を返します。  既定値は **false** です。  読み取り専用です。  
  
## 構文  
  
```  
  
rgExp.global  
```  
  
## 解説  
 必須の `rgExp` 参照は、**Regular Expression** オブジェクトのインスタンスです。  
  
 `global` プロパティは、正規表現のグローバル フラグが設定されているときは **true** を返し、設定されていないときは **false** を返します。  
  
 global フラグを使用すると、検索文字列内のパターンの最初の 1 候補だけではなく、すべての候補を検索できます。  これはグローバル マッチングとも呼びます。  
  
## 使用例  
 `global` プロパティの使用例を次に示します。  以下の関数に **g** を渡すと、"the" という単語がすべて "a" に置換されます。  **i** \(大文字と小文字の区別を無視\) フラグが関数に渡されていないため、文字列の先頭にある "The" は置換されません。  
  
 この関数は、設定可能な **g**、**i**、および **m** の各正規表現フラグに関連付けられたプロパティの条件を表示します。  また、すべての置換が適用された文字列も表示します。  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## 使用例  
 出力結果は次のようになります。  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 参照  
 [ignoreCase プロパティ \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline プロパティ \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)