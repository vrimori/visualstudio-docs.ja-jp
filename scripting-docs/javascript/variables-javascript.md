---
title: 変数 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1d09f634bd4901e4015766bf55f272926a0a31c
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="variables-javascript"></a>変数 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、変数に "hello" や 5 などの値が含まれています。 変数を使用して、`NumberOfDaysLeft = EndDate - TodaysDate` など、それが表すデータを参照します。  
  
 変数を使用して、コードに表示される値を格納、取得、および操作します。 変数にはわかりやすい名前を付け、だれが見てもコードの意味をすぐ理解できるようにします。  
  
## <a name="declaring-variables"></a>変数の宣言  
 変数がスクリプトに初めて出現するのは、それを宣言するときです。 変数は初めて記述されたときにメモリに設定されるので、それ以降、スクリプト内で参照できます。 変数は使用する前に宣言する必要があります。 そのためには、`var` キーワードを使用します。  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 `var` ステートメントで変数を初期化しない場合は、`undefined` の値が自動的に使用されます。  
  
## <a name="naming-variables"></a>変数の名前付け  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は大文字と小文字が区別される言語です。 つまり、**myCounter** などの変数名は、**MYCounter** という変数名とは異なります。 変数名は任意の長さにすることができます。 有効な変数名を作成するための規則は次のとおりです。  
  
-   最初の文字は、ASCII 文字 (大文字または小文字)、Unicode の変数の名前付け規則に準拠している文字、またはアンダースコア (_) 文字である必要があります。 先頭文字として数字を使用できないことに注意してください。  
  
-   2 文字目以降は、文字、数字、またはアンダースコア (_) にする必要があります。  
  
-   変数名を[予約語](../javascript/reference/javascript-reserved-words.md)にすることはできません。  
  
 有効な変数名の例をいくつか以下に示します。  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 無効な変数名の例をいくつか以下に示します。  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 変数を宣言して初期化するが、特定の値を指定しない場合は、`null` という値を割り当てます。 次に例を示します。  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 値を割り当てずに変数を宣言する場合、値は `undefined` になります。 次に例を示します。  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` 値は数字の 0 のように動作しますが、`undefined` は (数字ではなく) 特殊な値 `NaN` のように動作します。 `null` 値と `undefined` 値を比較した場合、これらは同等と見なされます。  
  
 宣言内で `var` キーワードを使用せずに変数を宣言し、値を割り当てることができます。 これは暗黙の宣言です。  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 宣言されていない変数を使用することはできません。  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>強制型変換  
 C++ のような厳密に型指定された言語とは対照的に、[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は柔軟に型指定された言語です。 これは、JavaScript の変数には定義済みの型がないことを意味します。 代わりに、変数の型がその値の型になります。 この動作により、値をさまざまな型のように処理できます。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、例外を発生させることなく、異なる型の値に対して操作を実行できます。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] インタープリターは、データ型の 1 つを他の型に暗黙的に変換するか*強制型変換*した後、演算を実行します。 文字列値、数値、およびブール値の強制型変換の規則は次のとおりです。  
  
-   数字と文字列を追加した場合、数字は文字列に強制的に変換されます。  
  
-   ブール値と文字列を追加した場合、ブール値は文字列に強制的に変換されます。  
  
-   数字とブール値を追加した場合、ブール値は数字に強制的に変換されます。  
  
 次の例では、文字列に追加された数字が文字列になります。  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 文字列は、比較のために同等の数字に自動的に変換されます。 文字列を整数に明示的に変換するには、[parseInt 関数](../javascript/reference/parseint-function-javascript.md)を使用します。 文字列を数字に明示的に変換するには、[parseFloat 関数](../javascript/reference/parsefloat-function-javascript.md)を使用します。