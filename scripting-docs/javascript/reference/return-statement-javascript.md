---
title: "return ステートメント (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function ステートメント"
  - "return ステートメント"
  - "return ステートメント, 終了 (関数をスクリプトで)"
  - "return ステートメント, 構文"
  - "実行の終了"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# return ステートメント (JavaScript)
現在の関数の実行を終了し、戻り値を返します。  
  
## 構文  
  
```  
  
return[(][expression][)];   
```  
  
## 解説  
 オプションの *expression* 引数は、関数から返される値です。  省略した場合、関数は戻り値を返しません。  
  
 `return` ステートメントを使用すると、関数の実行を中止し、*expression* の値を返すことができます。  *expression* を省略した場合、および関数内で `return` ステートメントが実行されなかった場合は、現在の関数を呼び出した式に undefined \(未定義\) 値が代入されます。  
  
## 使用例  
 次のコードは、`return` ステートメントの使用例です。  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## 使用例  
 次の例は、`return` ステートメントを使用して関数を戻す方法を示します。  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)