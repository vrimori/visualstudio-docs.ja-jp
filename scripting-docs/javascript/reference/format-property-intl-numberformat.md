---
title: "format プロパティ (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format プロパティ (Intl.NumberFormat)
指定された数値フォーマッタの設定を使用してロケール固有の数値の書式を設定する関数を返します。  
  
## 構文  
  
```  
numberFormatObj.format  
```  
  
#### パラメーター  
 `numberFormatObj`  
 必須。  フォーマッタとして使用する `NumberFormat` オブジェクトの名前。  
  
## 解説  
 `format` プロパティによって返される関数は、`value` という単一の引数を受け取り、`NumberFormat` オブジェクトで指定されたオプションを使用して、ローカライズされた数値を表す文字列を返します。  `value` を指定しない場合、この関数は `NaN` \(非数\) を返します。  
  
## 使用例  
 `NumberFormat` オブジェクトを使用して、ローカライズされた数値を作成する例を次に示します。  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [Intl.NumberFormat オブジェクト](../../javascript/reference/intl-numberformat-object-javascript.md)