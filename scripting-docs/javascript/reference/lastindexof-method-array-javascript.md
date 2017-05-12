---
title: "lastIndexOf メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript], lastIndexOf メソッド"
  - "lastIndexOf メソッド [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# lastIndexOf メソッド (Array) (JavaScript)
指定した値が配列内で最後に見つかった位置のインデックスを返します。  
  
## 構文  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須です。  検索する配列オブジェクト。|  
|`searchElement`|必須です。  `array1` 内で検索される値。|  
|`fromIndex`|省略可能です。  検索の開始位置を示す配列インデックス。  `fromIndex` を省略すると、検索は配列の最後のインデックスから開始されます。|  
  
## 戻り値  
 `searchElement` が配列内で最後に見つかった位置のインデックス。`searchElement` が見つからなかった場合は \-1。  
  
## 解説  
 `lastIndexOf` メソッドは、指定された値を配列で検索します。  メソッドは、最初に見つかった位置のインデックスを返します。指定された値が見つからない場合は \-1 を返します。  
  
 インデックスの降順に \(最後のメンバーを最初に\) 検索します。  昇順に検索するには、[indexOf メソッド \(Array\)](../../javascript/reference/indexof-method-array-javascript.md) を使用します。  
  
 配列要素は `===` の演算子での比較のような厳密等価で `searchElement` 値と比較されます。  詳細については、「[比較演算子](../../javascript/reference/comparison-operators-javascript.md)」を参照してください。  
  
 省略可能な `fromIndex` 引数には、検索を開始する配列インデックスを指定します。  `fromIndex` が配列の長さ以上である場合は、配列全体が検索されます。  `fromIndex` が負の場合、検索は配列の長さに `fromIndex` を加えた位置から開始されます。  計算されたインデックスが 0 未満の場合、\-1 が返されます。  
  
## 使用例  
 `lastIndexOf` メソッドの使用例を次に示します。  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [indexOf メソッド \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)