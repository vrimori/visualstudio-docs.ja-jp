---
title: "sort メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort メソッド"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# sort メソッド (Array) (JavaScript)
`Array` を並べ替えます。  
  
## 構文  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## Parameters  
 `arrayObj`  
 Required.  任意の `Array` オブジェクトを指定します。  
  
 `sortFunction`  
 Optional.  要素の順序を決定するために使用する関数の名前を指定します。  省略した場合、要素は ASCII 文字の昇順で並べ替えられます。  
  
## 戻り値  
 並べ替えられた配列。  
  
## 解説  
 `sort` メソッドは、指定された `Array` オブジェクト内の要素を並べ替えます。このメソッドを実行しても、新しい `Array` オブジェクトは作成されません。  
  
 引数 `sortFunction` を指定する場合は、次の戻り値を返すような関数を指定する必要があります。  
  
-   1 つ目の引数が 2 つ目の引数よりも小さい場合は、負の値を返す関数。  
  
-   2 つの引数が等しい場合は 0 を返す関数。  
  
-   1 つ目の引数が 2 つ目の引数よりも大きい場合は、正の値を返す関数。  
  
## 使用例  
 `sort` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]