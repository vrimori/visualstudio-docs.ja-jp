---
title: "indexOf メソッド (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "配列 [JavaScript], indexOf メソッド"
  - "indexOf メソッド [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# indexOf メソッド (Array) (JavaScript)
ある値が配列内で最初に見つかった位置のインデックスを返します。  
  
## 構文  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須です。  配列オブジェクト。|  
|`searchElement`|必須です。  `array1` 内で検索される値。|  
|`fromIndex`|省略可能です。  検索の開始位置を示す配列インデックス。  `fromIndex` を省略すると、検索はインデックス 0 から開始されます。|  
  
## 戻り値  
 `searchElement` が配列内で最初に見つかった位置のインデックス。`searchElement` が見つからなかった場合は \-1。  
  
## 解説  
 `indexOf` メソッドは、指定された値を配列で検索します。  メソッドは、最初に見つかった位置のインデックスを返します。指定された値が見つからない場合は \-1 を返します。  
  
 インデックスの昇順に検索します。  
  
 配列要素は `===` 演算子のような厳密等価で `searchElement` 値と比較されます。  詳細については、「[比較演算子](../../javascript/reference/comparison-operators-javascript.md)」を参照してください。  
  
 省略可能な `fromIndex` 引数には、検索を開始する配列インデックスを指定します。  `fromIndex` が配列の長さ以上である場合は、\-1 が返されます。  `fromIndex` が負の場合、検索は配列の長さに `fromIndex` を加えた位置から開始されます。  
  
## 使用例  
 `indexOf` メソッドの使用例を次に示します。  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)