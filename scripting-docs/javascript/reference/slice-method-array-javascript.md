---
title: "slice メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "0 から始まるインデックス"
  - "Array オブジェクト"
  - "slice メソッド"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# slice メソッド (Array) (JavaScript)
配列の一部を返します。  
  
## 構文  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## パラメーター  
 `arrayObj`  
 必須です。  `Array` オブジェクト。  
  
 `start`  
 必須です。  `arrayObj` から抽出する部分の先頭位置。  
  
 `end`  
 省略可能です。  `arrayObj` から抽出する部分の終端位置。  
  
## 解説  
 `slice` メソッドは、`arrayObj` の指定した部分が格納された `Array` オブジェクトを返します。  
  
 `slice` メソッドは、`end` 引数で指定した要素の 1 つ前の要素までをコピーします。  `start` に負の値を指定した場合、`length` \+ `start` として処理されます。`length` は配列の長さです。  `end` に負の値を指定した場合、`length` \+ `end` として処理されます。`length` は配列の長さです。  `end` を省略すると、`arrayObj` の最後までが抽出されます。  `end` で指定した抽出終了位置が `start` で指定した抽出開始位置より前に来る場合、要素は新しい配列にコピーされません。  
  
## 使用例  
 `slice` メソッドを使用する方法の例を次に示します。  最初の例では、`myArray` の最後の要素を除くすべてが `newArray` にコピーされます。  2 番目の例では、`myArray` の最後の 2 つの要素だけが `newArray` にコピーされます。  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [slice メソッド \(String\)](../../javascript/reference/slice-method-string-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)