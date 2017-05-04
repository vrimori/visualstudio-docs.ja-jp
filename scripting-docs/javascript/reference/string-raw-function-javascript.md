---
title: "String.raw 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.raw 関数 (JavaScript)
テンプレート文字列から未加工の文字列を返します。  
  
## 構文  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### パラメーター  
 `templateStr`  
 必須。  テンプレート文字列。  
  
 `obj`  
 必須。  { raw: 'value' }.などのオブジェクト リテラル表記を使用して指定された正しい形式のオブジェクト。  
  
 `...substitutions`  
 省略可能です。  1 つ以上の置換値で構成される配列 \([rest パラメーター](../../javascript/functions-javascript.md)\)。  
  
## 解説  
 `String.raw` 関数は、[テンプレート文字列](../../javascript/advanced/template-strings-javascript.md)と一緒に使用するよう意図されています。  未加工の文字列には、文字列内に存在するすべてのエスケープ文字と円記号が含まれます。  
  
 `obj` が正しい形式のオブジェクトではない場合には、エラーがスローされます。  
  
## 使用例  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]