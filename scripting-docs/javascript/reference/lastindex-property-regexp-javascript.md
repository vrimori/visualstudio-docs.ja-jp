---
title: "lastIndex プロパティ (RegExp) (JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex プロパティ"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# lastIndex プロパティ (RegExp) (JavaScript)
検索文字列内で次に文字が一致する位置を返します。  
  
## 構文  
  
```  
  
RegExp.lastIndex  
```  
  
## 解説  
 このプロパティに関連付けられるオブジェクトは、常にグローバルな `RegExp` オブジェクトです。  
  
 `lastIndex` プロパティの値は、文字列の先頭位置の 0 を基にしています。  初期値は –1 です。  この値は、検索が成功するたびに変更されます。  
  
 `lastIndex` プロパティは、`RegExp` オブジェクトの `exec` メソッドと **test** メソッド、および `String` オブジェクトの `match` メソッド、**replace** メソッド、および **split** メソッドによって変更されます。  
  
 `lastIndex` プロパティの値には、次の規則が適用されます。  
  
-   一致する文字列がない場合、`lastIndex` は \-1 に設定されます。  
  
-   `lastIndex` プロパティの値を文字列よりも長く設定してから **test** メソッドまたは `exec` メソッドを実行すると、メソッドの実行は失敗し、`lastIndex` プロパティに \-1 が設定されます。  
  
-   `lastIndex` プロパティの値が文字列の長さと等しい場合、パターンが空の文字列であれば、正規表現パターンが一致します。  それ以外の場合、検索は失敗し、`lastIndex` プロパティに \-1 が再設定されます。  
  
-   上記以外の場合、`lastIndex` プロパティは、パターンに一致する最後に見つかった文字列の直後の位置を示す値が設定されます。  
  
## 使用例  
 `lastIndex` プロパティの使用例を次に示します。  この関数は、文字列の検索を繰り返し、文字列内にある各文字の **index** 値および `lastIndex` 値を出力します。  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## 参照  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)