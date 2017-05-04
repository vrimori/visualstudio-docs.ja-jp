---
title: "match メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match メソッド"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# match メソッド (String) (JavaScript)
正規表現パターンを使って文字列に対して一致検索を実行し、検索結果を格納する配列を戻します。  
  
## 構文  
  
```  
  
stringObj.match(rgExp)   
```  
  
## パラメーター  
 `stringObj`  
 必須です。  検索対象とする `String` オブジェクトの名前またはリテラル文字列を指定します。  
  
 `rgExp`  
 必須です。  正規表現パターンおよび適用できるフラグを含む、正規表現オブジェクトを指定します。  このオブジェクトは、正規表現パターンとフラグを含む、変数名または文字列リテラルにもなります。  
  
## 解説  
 パターンに一致する文字列が見つからなかった場合、`match` メソッドは `null` を返します。  一致する文字列が見つかった場合、`match` は配列を返し、さらにグローバルな `RegExp` オブジェクトのプロパティが検索結果を反映して更新されます。  
  
 グローバル フラグ \(`g`\) が設定されていない場合、配列の要素 0 には一致した文字列全体が、要素 1 から *n* には、一致した文字列の中に副次的に含まれている内容が格納されます。  この動作は、グローバル フラグが設定されていない場合の [exec メソッド \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md) の動作と同じです。  グローバル フラグが設定されている場合、要素 0 から *n* には一致したすべての文字列がそれぞれ格納されます。  
  
 グローバル フラグが設定されていない場合、`match` のメソッドが返す配列には `input`、および `index` の 2 つのプロパティがあります。  `input` プロパティには、検索された文字列全体が格納されます。  `index` プロパティには、検索された文字列内の一致した部分文字列の位置が格納されます。  
  
 フラグ `i` が設定されている場合は、検索で大文字と小文字が区別されません。  
  
## 使用例  
 `match` メソッドの使用例を次に示します。  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [exec メソッド \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace メソッド \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [search メソッド \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test メソッド \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ja-jp/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/ja-jp/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/ja-jp/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)