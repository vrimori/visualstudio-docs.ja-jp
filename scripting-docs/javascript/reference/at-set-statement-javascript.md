---
title: "@set ステートメント (JavaScript) | Microsoft Docs"
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
  - "@set_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@set ステートメント"
  - "条件付きコンパイル, 変数"
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# @set ステートメント (JavaScript)
条件付きコンパイル ステートメントで使用する変数を作成します。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 標準モードと [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  条件付きコンパイルは、Internet Explorer 10 標準モードと、それ以前のすべてのバージョンでサポートされています。  
  
## 構文  
  
```  
  
@set @varname = term   
```  
  
## パラメーター  
 *varname*  
 必須。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で有効な変数名を指定します。  必ず先頭に "@" という文字を記述します。  
  
 `term`  
 必ず指定します。  0 個以上の単項演算子に続けて、定数、条件コンパイル変数、またはかっこで囲んだ式を指定します。  
  
## 解説  
 条件コンパイルでは、数値変数とブール変数がサポートされています。  文字列はサポートされていません。  通常、`@set` ステートメントで作成した変数は、条件コンパイルの中で使用しますが、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードのどの場所でも使用できます。  
  
 変数宣言のコード例を次に示します。  
  
```javascript  
  
        @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 かっこで囲んだ式の中で使用できる演算子は次のとおりです。  
  
-   `!  ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 まだ定義していない変数を使用すると、その値は `NaN` になります。  `@if` ステートメントを次のコード例のように使用すると、値が `NaN` かどうかを確認できます。  
  
```javascript  
@if (@newVar != @newVar)  
   ...  
```  
  
 `NaN` は、自身と比較しても等しいと評価されない唯一の値で、コードによって確認できます。  
  
## 必要条件  
 Internet Explorer のすべてのバージョンでサポートされていますが、[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  
  
## 参照  
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件付きコンパイル変数](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on ステートメント](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if ステートメント](../../javascript/reference/at-if-statement-javascript.md)