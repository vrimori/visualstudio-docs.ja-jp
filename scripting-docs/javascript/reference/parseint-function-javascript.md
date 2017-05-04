---
title: "parseInt 関数 (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt メソッド"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# parseInt 関数 (JavaScript)
文字列を整数に変換します。  
  
## 構文  
  
```  
parseInt(numString, [radix])   
```  
  
## パラメーター  
 `numString`  
 必須です。  数値に変換する文字列を指定します。  
  
 `radix`  
 省略可能です。  `numString` 内の数値の基数を指定する 2 ～ 38 の値。  この引数を指定しなければ、先頭に '0x' が付いている文字列は 16 進数と見なされます。  これ以外の文字列は、10 進数と見なされます。  
  
## 解説  
 `parseInt` 関数は、`numString` 引数に格納されている数値に等しい整数値を返します。  `numString` 引数の先頭に整数がない場合は、`NaN` \(非数値\) を返します。  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 値が `NaN` かどうかを調べるには、`isNaN` 関数を使用します。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] より、`parseInt` 関数は、先頭が '0' の文字列を 8 進数として処理しません。  ただし、`parseInt` 関数を使用しない場合は、先頭が '0' の文字列を 8 進数として解釈できます。  8 の整数については、「[データ型](../../javascript/data-types-javascript.md)」を参照してください。  
  
## 参照  
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat 関数](../../javascript/reference/parsefloat-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [valueOf メソッド \(Object\)](../../javascript/reference/valueof-method-object-javascript.md)