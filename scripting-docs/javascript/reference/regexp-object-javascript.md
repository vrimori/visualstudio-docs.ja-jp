---
title: "RegExp オブジェクト (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp オブジェクト"
  - "RegExp オブジェクト, 概要"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# RegExp オブジェクト (JavaScript)
正規表現パターン一致の結果についての情報を保存する組み込みのグローバルなオブジェクトです。  
  
## 構文  
  
```  
  
RegExp.property   
```  
  
## 解説  
 必須の *property* 引数には、`RegExp` オブジェクトのいずれかのプロパティを指定できます。  
  
 `RegExp` オブジェクトは、直接作成することはできませんが、いつでも使用できます。  正規表現の検索が成功するまでの `RegExp` オブジェクトのさまざまなプロパティの初期値を次の表に示します。  
  
|プロパティ|略式|初期値|  
|-----------|--------|---------|  
|index||\-1|  
|input|$\_|空の文字列|  
|lastIndex||\-1|  
|lastMatch|$&|空の文字列|  
|lastParen|$\+|空の文字列|  
|leftContext|$\`|空の文字列|  
|rightContext|$'|空の文字列|  
|$1 \- $9|$1 \- $9|空の文字列|  
  
 このプロパティは、正規表現の検索が正常に完了するまで値としては定義されません。  
  
 グローバルな `RegExp` オブジェクトを **Regular Expression** オブジェクトと混同しないようにしてください。  これらは同じのように見えますが明確な違いがあります。  グローバルな `RegExp` オブジェクトのプロパティには、一致が検出されるたびに更新される情報が格納されるのに対し、**Regular Expression** オブジェクトのプロパティには、**Regular Expression** のそのインスタンスによる一致に関する情報だけが格納されます。  
  
## 使用例  
 正規表現の検索を実行する例を次に示します。  この例では、グローバルな `RegExp` オブジェクトおよび `exec` メソッドによって返される配列から一致とサブマッチを表示します。  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
<a name="js56jsobjregexpprop"></a>   
## プロパティ  
 [$1...$9 プロパティ](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index プロパティ](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input プロパティ](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex プロパティ](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch プロパティ](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen プロパティ](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext プロパティ](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext プロパティ](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## メソッド  
 `RegExp` オブジェクトには、メソッドはありません。  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)