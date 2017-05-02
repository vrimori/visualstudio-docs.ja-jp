---
title: "Math.abs 関数 (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "絶対値、計算"
  - "絶対値"
  - "数式"
  - "abs メソッド"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Math.abs 関数 (JavaScript)
数値の絶対値 \(正と負が考慮されない値\) を返します。  たとえば、\-5 の絶対値と 5 の絶対値は同じです。  
  
## 構文  
  
```  
Math.abs(number)  
```  
  
#### パラメーター  
 必須の `number` 引数は、絶対値を求める数式です。  
  
## 戻り値  
 `number` 引数の絶対値。  
  
## 使用例  
 `abs` 関数の使用例を次に示します。  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 参照  
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)