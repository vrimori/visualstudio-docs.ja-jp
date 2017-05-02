---
title: "multiline プロパティ (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline プロパティ"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# multiline プロパティ (Regular Expression) (JavaScript)
正規表現で使用する multiline フラグ \(**m**\) の状態を表すブール値を返します。  既定値は **false** です。  読み取り専用です。  
  
## 構文  
  
```  
  
rgExp.multiline  
```  
  
## 解説  
 必須の `rgExp` 引数は、`RegExp` オブジェクトのインスタンスです。  
  
 **multiline** プロパティは、正規表現の multiline フラグが設定されている場合は **true** を返し、設定されていない場合は **false** を返します。  **m** フラグを使用して正規表現オブジェクトを作成すると、**multiline** プロパティが **true** になります。  
  
 **multiline** が **false** の場合、"^" は文字列の先頭位置に一致し、"$" は文字列の最終位置に一致します。  **multiline** が **true** の場合、"^" は "\\n" または "\\r" の直後を含む文字列の先頭位置に一致し、"$" は "\\n" または "\\r" の直前を含む文字列の最終位置に一致します。  
  
## 使用例  
 **multiline** プロパティの動作の例を次に示します。  以下の関数に "m" を渡すと、"while" という単語が "and" に置換されます。  これは、multiline フラグが設定されていて、改行文字の後の行頭に "while" があるためです。  multiline フラグを設定すると、複数行文字列に対して検索を実行できます。  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 参照  
 [global プロパティ \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase プロパティ \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)