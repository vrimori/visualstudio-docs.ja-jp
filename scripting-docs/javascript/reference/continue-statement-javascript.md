---
title: "continue ステートメント (JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue ステートメント"
  - "do...while ステートメント"
  - "ループ構造, continue ステートメント"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# continue ステートメント (JavaScript)
ループの現在の反復の実行を中止し、次の反復の実行を開始します。  
  
## 構文  
  
```  
continue [label];  
```  
  
## 解説  
 `label` 引数は省略可能で、`continue` を適用するステートメントを指定します。  
  
 `continue` ステートメントは、`while` ループ、`do...while` ループ、**for** ループ、または `for...in` ループの中だけで使用できます。  `continue` ステートメントを実行すると、ループの現在の反復の実行が中止され、プログラムの実行はループの先頭から続行されます。  このステートメントの動作は、次のようにループの種類により少しずつ異なります。  
  
-   `while` ループと `do...while` ループでは、条件が評価され、その結果が true の場合はループの実行が繰り返されます。  
  
-   `for` ループでは、最初にインクリメント式が実行され、次に条件式が true の場合はループの実行が繰り返されます。  
  
-   `for...in` ループでは、指定された変数の次のフィールドに進み、ループの実行が繰り返されます。  
  
## 例  
 ループを 1 ～ 9 まで繰り返す例を次に示します。  `(i < 5)` 式と共に `continue` ステートメントが使用されているため、`continue` から `for` 本体の最後までのステートメントはスキップされます。  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 次のコードでは、`continue` ステートメントは、`Inner:` ラベルが前に付いている `for` ループを参照します。  `j` が 24 に達すると、`continue` ステートメントによって `for` ループが次の反復処理に移ります。  各行には 21 ～ 23 と 25 ～ 30 の数字が出力されます。  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [do...while ステートメント](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [ラベル付きステートメント](../../javascript/reference/labeled-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)