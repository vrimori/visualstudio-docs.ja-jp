---
title: "Number 定数 (JavaScript) | Microsoft Docs"
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
  - "定数 [JavaScript], 数値"
  - "MAX_VALUE 定数 [JavaScript]"
  - "MIN_VALUE 定数 [JavaScript]"
  - "NaN 定数 [JavaScript]"
  - "NEGATIVE_INFINITY 定数 [JavaScript]"
  - "number 定数 [JavaScript]"
  - "Number.MAX_VALUE 定数 [JavaScript]"
  - "Number.MIN_VALUE 定数 [JavaScript]"
  - "Number.NaN 定数 [JavaScript]"
  - "Number.NEGATIVE_INFINITY 定数 [JavaScript]"
  - "Number.POSITIVE_INFINITY 定数 [JavaScript]"
  - "POSITIVE_INFINITY 定数 [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Number 定数 (JavaScript)
次の数値定数は、`Number` オブジェクトのプロパティです。  
  
## 数値オブジェクト定数  
 これらの定数にアクセスするために `Number` オブジェクトを作成する必要はありません。  
  
|定数|返される値|  
|--------|-----------|  
|`Number.EPSILON`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる最小の数値。  約 2.2204460492503130808472633361816E\-16。|  
|`Number.MAX_SAFE_INTEGER`|JavaScript で安全に表現できる最大の数値。  9007199254740991 と等価です。|  
|`Number.MAX_VALUE`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる最大の数値。  約 1.79E\+308。|  
|`Number.MIN_SAFE_INTEGER`|JavaScript で安全に表現できる最小の数値。  −9007199254740991 と等価です。|  
|`Number.MIN_VALUE`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せるゼロに最も近い数値。  約 5.00E\-324。|  
|`Number.NaN`|数値以外の値<br /><br /> 等価比較では、`NaN` は、それ自体を含めいずれの値とも等しくありません。  値が `NaN` と等しいかどうかをテストするには、[isNaN 関数](../../javascript/reference/isnan-function-javascript.md)を使用します。|  
|`Number.NEGATIVE_INFINITY`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる負の最大数値より小さい値。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、`NEGATIVE_INFINITY` 値を `-infinity` として表示します。|  
|`Number.POSITIVE_INFINITY`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる最大数値より大きい値。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、`POSITIVE_INFINITY` 値を `infinity` として表示します。|  
  
## 要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 `Number.EPSILON`、`Number.MAX_SAFE_INTEGER`、および `Number.MIN_SAFE_INTEGER` の場合:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **対象**: [Number オブジェクト](../../javascript/reference/number-object-javascript.md)  
  
## 参照  
 [数値演算定数](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript 定数](../../javascript/reference/javascript-constants.md)   
 [定数 Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN 定数](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)