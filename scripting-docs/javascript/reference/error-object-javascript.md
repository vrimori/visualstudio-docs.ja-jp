---
title: "Error オブジェクト (JavaScript) | Microsoft Docs"
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
  - "Error"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Error オブジェクト"
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Error オブジェクト (JavaScript)
エラーに関する情報を格納します。  
  
## 構文  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## パラメーター  
 `errorObj`  
 必須です。  `Error` オブジェクトを代入する変数名を指定します。  変数代入は `throw` ステートメントを使用してエラーを作成するときには省略されます。  
  
 `number`  
 省略可能です。  エラーに割り当てられる数値を指定します。  省略した場合は 0 です。  
  
 `description`  
 省略可能です。  エラーを説明する短い文字列を指定します。  省略した場合は空の文字列です。  
  
## 解説  
 ランタイム エラーが発生した場合はいつでも、エラーを記述する `Error` オブジェクトのインスタンスが作成されます。  このインスタンスには、エラー \(`description` プロパティ\) およびエラー番号 \(`number` プロパティ\) の説明を含む 2 種類の組み込みプロパティがあります。  詳細については、「[JavaScript ランタイム エラー](../../javascript/reference/javascript-run-time-errors.md)」を参照してください。  
  
 エラー番号は 32 ビット値です。  上位の 16 ビット ワードは機能識別符号です。下位のワードは実際のエラー コードです。  
  
 `Error` オブジェクトは、前の構文を使用して明示的に作成することも、`throw` ステートメントを使用してスローすることもできます。  どちらの場合も、選択した任意のプロパティを追加して、`Error` オブジェクトの機能を拡張できます。  
  
 通常、**try...catch** ステートメントで作成されたローカル変数は、暗黙的に作成された `Error` オブジェクトを参照します。  したがって、エラー番号と説明を任意の方法で使用できます。  
  
## 使用例  
 次のコードは、`Error` オブジェクトの使用例です。  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## 使用例  
 次の例は、暗黙的に作成された `Error` オブジェクトの使用方法を示します。  
  
```javascript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## メソッド  
 [toString メソッド \(エラー\)](../../javascript/reference/tostring-method-error.md) &#124; [valueOf メソッド \(日付\)](../../javascript/reference/valueof-method-date.md)  
  
## プロパティ  
 [constructor プロパティ \(エラー\)](../../javascript/reference/constructor-property-error.md) &#124; [description プロパティ](../../javascript/reference/description-property-error-javascript.md) &#124; [message プロパティ](../../javascript/reference/message-property-error-javascript.md) &#124; [name プロパティ](../../javascript/reference/name-property-error-javascript.md) &#124; [number プロパティ](../../javascript/reference/number-property-error-javascript.md) &#124; [prototype プロパティ \(エラー\)](../../javascript/reference/prototype-property-error.md) &#124; [stack プロパティ \(Error\)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stackTraceLimit プロパティ \(Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 参照  
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally ステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var ステートメント](../../javascript/reference/var-statement-javascript.md)   
 [Hilo JavaScript のサンプル アプリ \(Windows ストア\)](http://hilojs.codeplex.com/SourceControl/latest)