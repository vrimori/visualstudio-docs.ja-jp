---
title: "switch ステートメント (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch ステートメント"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# switch ステートメント (JavaScript)
指定した式の値がラベルと一致したときに 1 つ以上のステートメントを実行する機能を提供します。  
  
## 構文  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## パラメーター  
 `expression`  
 評価される式を指定します。  
  
 `label`  
 `expression` と照合される識別子を指定します。  `label` が `expression` である場合は、コロンの直後の `statementlist` の実行が開始され、`break` ステートメント \(省略可能です\) が見つかった箇所か、`switch` ステートメントの最後まで実行されます。  
  
 `statementlist`  
 実行する 1 つ以上のステートメントを指定します。  
  
## 解説  
 どのラベルの値も `expression` の値と一致しなかった場合に実行するステートメントを指定するには、`default` 句を使用します。  これは、`switch` コード ブロック内のどこでも記述できます。  
  
 `label` で指定するブロックの数に制限はありません。  `expression` の値がどの `label` の値にも一致せず、`default` 句も指定していなかった場合は、ステートメントは実行されません。  
  
 `switch` ステートメントでの実行の流れは次のようになります。  
  
-   `expression` が評価され、この式に一致するものが見つかるまで、順序どおりに `label` が評価されます。  
  
-   `label` 値が `expression` と等しい場合は、その直後に記述された `statementlist` が実行されます。  
  
     実行は、`break` ステートメントが実行されるか、`switch` ステートメントが終了するまで続行されます。  つまり、`break` ステートメントを記述しない場合は、複数の `label` ブロックが実行されます。  
  
-   `expression` と等しい `label` がまったくない場合は、`default` 句に進みます。  `default` 句がない場合は、最後のステップに進みます。  
  
-   `switch` コード ブロックの末尾の次のステートメントから実行を続けます。  
  
## 使用例  
 オブジェクトの型を調べる例を次に示します。  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## 使用例  
 `break` ステートメントを使用しない場合に実行される処理を次のコードに示します。  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [if...else ステートメント](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)