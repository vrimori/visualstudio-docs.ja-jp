---
title: "isNaN 関数 (JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN メソッド"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# isNaN 関数 (JavaScript)
指定した値が予約済みの値 `NaN` \(非数\) かどうかを表すブール値を返します。  
  
## 構文  
  
```  
isNaN(numValue)   
```  
  
## 戻り値  
 `Number` 型に変換された値が `NaN` の場合は `true`、それ以外の場合は `false`。  
  
## 解説  
 必須の `numValue` は、`NaN` に対して評価される値です。  
  
 通常、`parseInt` メソッドや `parseFloat` メソッドからの戻り値を調べるために使用します。  
  
 また、`NaN` または別の値を含む変数をそれ自身と比較して、NaN かどうかを調べることもできます。  値が等しいと評価されない場合、その変数は `NaN` となります。  `NaN` は、自身と比較して等しいと評価されない唯一の値です。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 使用例  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## 参照  
 [isFinite 関数](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN 定数](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat 関数](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt 関数](../../javascript/reference/parseint-function-javascript.md)