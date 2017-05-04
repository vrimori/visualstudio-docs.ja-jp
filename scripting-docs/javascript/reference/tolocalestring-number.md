---
title: "toLocaleString (Number) | Microsoft Docs"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (Number)
現在のロケールまたは指定されたロケールでの既定の書式を使用して、数値を文字列に変換します。  
  
## 構文  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### パラメーター  
 `numberObj`  
 Required.  変換対象の `Number` オブジェクト。  
  
 `locales`  
 省略可能。  1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。  複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。  このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  
  
 `options`  
 省略可能。  比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。  
  
## 解説  
 Internet Explorer 11 以降では、`toLocaleString` は、`locales` パラメーターと `options` パラメーターのサポートを追加する `Intl.NumberFormat` を内部的に使用して、比較を実行します。  これらのパラメーターの詳細については、「[Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)」を参照してください。  
  
> [!IMPORTANT]
>  `locales` パラメーターと `options` パラメーターは、一部のドキュメント モードとブラウザー バージョンではサポートされていません。  詳細については、「必要条件」を参照してください。  
  
> [!NOTE]
>  `locales` パラメーターを省略する場合、`toLocaleString` はユーザーに結果を表示する目的だけで使用してください。この関数の結果はコンピューターによって異なるため \(このメソッドは現在のロケールを返します\)、スクリプト内で値を計算する目的では使用しないでください。  
  
## 使用例  
 次の例は、パラメーターを指定せずに `toLocaleString` メソッドを使用する方法を示します。  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## 使用例  
 次の例は、ロケールと比較オプションを指定して `toLocaleString` メソッドを使用する方法を示します。  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` パラメーターと `options` パラメーター:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [toLocaleDateString メソッド \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)