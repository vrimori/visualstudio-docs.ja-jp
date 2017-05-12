---
title: "undefined 定数 (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined プロパティ"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# undefined 定数 (JavaScript)
初期化されていない変数など、定義されていない値。  
  
## 構文  
  
```  
undefined  
```  
  
## 解説  
 `undefined` 定数は `Global` オブジェクトのメンバーで、スクリプト エンジンが初期化されたときに使用できるようになります。  変数を宣言し、初期化していない場合、その値は **undefined** になります。  
  
 変数を宣言していない場合、その変数と `undefined` は比較できません。ただし、その変数の型と文字列 "undefined" は比較できます。  
  
 `undefined` 定数は、変数に undefined を明示的に設定するときまたはテストするときに便利です。  
  
## 使用例  
 `undefined` 定数を使用する方法の例を次に示します。  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## 必要条件  
 `undefined` プロパティは [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)] で導入され、[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] で読み取り専用になりました。  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 参照  
 [typeof 演算子](../../javascript/reference/typeof-operator-decrementjavascript.md)