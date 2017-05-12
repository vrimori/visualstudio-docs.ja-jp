---
title: "input プロパティ ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_ プロパティ"
  - "input プロパティ"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# input プロパティ ($_) (RegExp) (JavaScript)
正規表現検索の対象となった文字列を返します。  読み取り専用です。  
  
## 構文  
  
```  
  
RegExp.input  
```  
  
## 解説  
 このプロパティに関連付けられるオブジェクトは、常にグローバルな `RegExp` オブジェクトです。  
  
 **input** プロパティの値は、検索文字列が変更されるたびに変更されます。  
  
 **input** プロパティの使用例を次に示します。  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## 参照  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)