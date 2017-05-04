---
title: "ignoreCase プロパティ (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase プロパティ"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ignoreCase プロパティ (Regular Expression) (JavaScript)
正規表現で使用する ignoreCase フラグ \(**i**\) の状態を表すブール値を返します。  既定値は **false** です。  読み取り専用です。  
  
## 構文  
  
```  
  
rgExp.ignoreCase  
```  
  
## 解説  
 `rgExp` の必須の参照は、`RegExp` オブジェクトのインスタンスです。  
  
 **ignoreCase** プロパティは、正規表現の ignoreCase フラグが設定されている場合は **true** を返し、設定されていない場合は **false** を返します。  
  
 ignoreCase フラグを使用すると、検索文字列内のパターンをマッチングさせるときに、大文字小文字の区別をしません。  
  
## 使用例  
 **ignoreCase** プロパティの使用例を次に示します。  以下の関数に "gi" を渡すと、先頭の "The" も含めて "the" という単語のすべてのインスタンスが "a" に置換されます。  これは、ignoreCase フラグが設定されていると、検索時に大文字と小文字の区別が無視されるためです。  したがって、"T" はマッチングにおいて "t" と同じです。  
  
 この関数は、設定可能な **g**、**i**、および **m** の各正規表現フラグの状態を示すブール値を返します。  すべての置換が適用された文字列も返します。  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## 使用例  
 出力結果は次のようになります。  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 参照  
 [global プロパティ \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline プロパティ \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)