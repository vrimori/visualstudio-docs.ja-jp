---
title: "for ステートメント (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ループ構造, for ステートメント"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# for ステートメント (JavaScript)
指定された条件が true の間、複数のステートメントから構成されるブロックを繰り返し実行します。  
  
## 構文  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## パラメーター  
 `initialization`  
 省略可能です。  任意の式を指定します。  この式は、ループを実行する直前に一度だけ実行されます。  
  
 `test`  
 省略可能です。  ブール式を指定します。  `test` が `true` の場合は、`statement` が実行されます。  `test` が `false` の場合、ループ処理は終了します。  
  
 `increment`  
 省略可能です。  任意の式を指定します。  インクリメント式は、ループ内のブロックの実行が終わるたびに実行されます。  
  
 `statement`  
 省略可能です。  `test` が **true** の場合に実行する 1 つ以上のステートメント。  複合ステートメントを指定することもできます。  
  
## 解説  
 特定の回数だけ処理を繰り返す場合は、`for` ループを使用します。  `for` ループは、配列を繰り返し処理する場合および順次処理を実行する場合に便利です。  
  
 条件式をテストした後にループが実行されるので、`for` ステートメントは 0 回以上実行されます。  
  
 `for` ループ ステートメント ブロック内の任意の行で、`break` ステートメントを使用してループから抜けることができます。同様に、任意の行で `continue` ステートメントを使用して、ループの次の反復処理に制御を移すことができます。  
  
## 使用例  
 次の例では、`for` ステートメントは、かっこで囲まれたステートメントを次のように実行します。  
  
-   最初に、`i` 変数の初期値が評価されます。  
  
-   次に、`i` の値が 9 以下であれば、`document.write` ステートメントが実行され、`i` が再評価されます。  
  
-   `i` が 9 より大きい場合は条件が false になり、制御がループの外に移ります。  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## 使用例  
 `for` ステートメントの式はすべて省略可能です。  次の例では、`for` ステートメントで無限ループを作成し、`break` ステートメントを使用してループを終了します。  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)