---
title: "index プロパティ (RegExp) (JavaScript) | Microsoft Docs"
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
  - "index"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Index プロパティ"
  - "対応する文字列"
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# index プロパティ (RegExp) (JavaScript)
検索された文字列で最初の一致が開始される文字の位置を返します。  読み取り専用です。  
  
## 構文  
  
```  
  
RegExp.index   
```  
  
## 解説  
 このプロパティに関連付けられるオブジェクトは、常にグローバルな `RegExp` オブジェクトです。  
  
 **index** プロパティの値は、0 から始まるインデックス番号です。  **index** プロパティの初期値は –1 です。  この値は、検索が成功するたびに変更されます。  
  
## 使用例  
 **index** プロパティの使用例を次に示します。  この関数は、文字列の検索を繰り返し、文字列内にある各文字の **index** 値および `lastIndex` 値を出力します。  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## 参照  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)