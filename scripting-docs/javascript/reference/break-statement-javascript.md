---
title: "break ステートメント (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break ステートメント"
  - "do...while ステートメント"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# break ステートメント (JavaScript)
現在のループを終了します。または、`label` が指定されている場合は、関連するステートメントを終了します。  
  
## 構文  
  
```  
break [label];  
```  
  
## 解説  
 省略可能な `label` 引数で、終了するステートメントのラベルを指定します。  
  
 通常、`break` ステートメントは、`switch` ステートメント、`while` ループ、`for` ループ、`for...in` ループ、または `do...while` ループの中で使用します。  `label` 引数は、`switch` ステートメントの中で頻繁に使用しますが、単純なステートメントや複合ステートメントなど任意のステートメントの中でも使用できます。  
  
 `break` ステートメントを実行すると、現在のループまたはステートメントの実行が終了し、直後のステートメントからスクリプトの実行が開始されます。  
  
## 例  
 この例では、カウンターは 1 から 99 までカウントするように設定されています。ただし、`break` ステートメントによってループは 14 回で終了します。  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 次のコードでは、`break` ステートメントは、`Inner:` ステートメントが前に付いた `for` ループを参照しています。  `j` が 24 に達すると、`break` ステートメントが実行され、そのループが終了します。  各行には 21 ～ 23 の数字が出力されます。  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)   
 [do...while ステートメント](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [ラベル付きステートメント](../../javascript/reference/labeled-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)