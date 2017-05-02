---
title: "変数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "大文字と小文字の区別, JavaScript 変数名"
  - "強制変換"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 変数 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、変数に "hello" や 5 などの値が含まれています。  変数を使用して、たとえば `NumberOfDaysLeft = EndDate – TodaysDate` など、それが表すデータを参照します。  
  
 変数を使用して、コードに表示される値を格納、取得、操作します。  変数にはわかりやすい名前を付けて、だれが見てもコードの意味をすぐ理解できるようにしてください。  
  
## 変数の宣言  
 変数がスクリプトに初めて出現するのは、それを宣言するときです。  変数は初めて記述されたときにメモリに設定されるので、それ以降、スクリプト内で参照できます。  変数は、使用する前に宣言する必要があります。  このためには、`var` キーワードを使用します。  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 `var` ステートメントで変数を初期化しない場合は、自動的に値が `undefined` になります。  
  
## 変数の名前付け  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は、大文字と小文字を区別する言語です。  つまり、myCounter のような変数名は、変数名 MYCounter とは異なります。  変数名の長さに制限はありません。  有効な変数名を作成するための規則を次に示します。  
  
-   先頭文字は、ASCII 文字 \(大文字でも小文字でもかまいません\) またはアンダースコア \(\_\) 文字にする必要があります。  先頭文字として数値を使用することはできません。  
  
-   2 文字目以降の文字には、英字、数字、アンダースコア \(\_\) を使用できます。  
  
-   [予約語](../javascript/reference/javascript-reserved-words.md)は変数名に使用できません。  
  
 有効な変数名の例を次に示します。  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 無効な変数名の例を次に示します。  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 変数を宣言して初期化するだけで、特定の値を指定しない場合は、値 `null` を代入します。  次に例を示します。  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 値を代入せずに変数を宣言する場合、値は `undefined` になります。  次に例を示します。  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` 値は、数値 0 のように動作し、`undefined` は特殊な値 `NaN` \(非数\) のように動作します。  `null` 値と `undefined` 値を比較すると、それらは等しいと判断されます。  
  
 宣言内で `var` キーワードを使用せずに変数を宣言して、それに値を代入できます。  これは暗黙の宣言です。  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 宣言されていない変数を使用することはできません。  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## 強制型変換  
 C\+\+ のような厳密に型指定された言語とは対照的に、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は柔軟に型指定された言語です。  これは、JavaScript の変数には定義済みの型がないことを意味します。  代わりに、値の型が変数の型になります。  この動作により、値をさまざまな型のように処理できます。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、例外が発生することなく、異なる型の値に対して演算を実行できます。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] インタープリターは、データ型の 1 つを他の型に暗黙的に変換するか*強制型変換*した後、演算を実行します。  文字列値、数値、およびブール値の強制型変換の規則を次に示します。  
  
-   数値と文字列を追加すると、数値は文字列に強制的に変換されます。  
  
-   ブール値と文字列を追加すると、ブール値は文字列に強制的に変換されます。  
  
-   数値とブール値を追加すると、ブール値は数値に強制的に変換されます。  
  
 次の例では、文字列に追加される数値が文字列になります。  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 文字列は、比較のために等価の数値に自動的に変換されます。  文字列を明示的に整数に変換するには、[parseInt 関数](../javascript/reference/parseint-function-javascript.md)を使用します。  文字列を明示的に数値に変換するには、[parseFloat 関数](../javascript/reference/parsefloat-function-javascript.md)を使用します。