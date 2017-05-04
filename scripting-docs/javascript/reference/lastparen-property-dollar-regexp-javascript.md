---
title: "lastParen プロパティ ($+) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastParen プロパティ ($+)"
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# lastParen プロパティ ($+) (RegExp) (JavaScript)
正規表現による検索で、最後にパターン化されたサブマッチがある場合に、それを返します。  読み取り専用です。  
  
## 構文  
  
```  
  
RegExp.lastParen  
```  
  
## 解説  
 このプロパティに関連付けられるオブジェクトは、常にグローバルな `RegExp` オブジェクトです。  
  
 `lastParen` プロパティの初期値は空の文字列です。  `lastParen` プロパティの値は、検索が成功するたびに変更されます。  
  
## 使用例  
 `lastParen` プロパティの使用例を次に示します。  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## 参照  
 [$1...$9 プロパティ \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index プロパティ \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input プロパティ \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex プロパティ \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch プロパティ \($&\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [leftContext プロパティ \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext プロパティ \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)