---
title: "toLocaleTimeString メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleTimeString メソッド"
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toLocaleTimeString メソッド (Date) (JavaScript)
ホスト環境の現在のロケールまたは指定されたロケールに対応した時刻を文字列値で返します。  
  
## 構文  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### パラメーター  
 `dateObj`  
 必須。  `Date` オブジェクト。  
  
 `locales`  
 省略可能です。  1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。  複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。  このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  
  
 `options`  
 省略可能です。  比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。  
  
## 解説  
 Internet Explorer 11 以降では、`toLocaleTimeString` は、`Intl.DateTimeFormat` パラメーターと `locales` パラメーターのサポートを追加する `options` を内部的に使用して、時刻の書式を設定します。  これらのパラメーターの詳細については、「[Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)」を参照してください。  
  
> [!IMPORTANT]
>  `locales` パラメーターと `options` パラメーターは、一部のドキュメント モードとブラウザー バージョンではサポートされていません。  詳細については、「必要条件」を参照してください。  
  
 Internet Explorer 10 標準ドキュメント モード、以前のドキュメント モード、および互換捻出モードで `toLocaleTimeString` を使用すると、次のようになります。  
  
-   現在のタイム ゾーンでの時刻を含む文字列値が返されます。  
  
-   返される時刻の形式は、ホスト環境の現在のロケールの既定形式になります。  
  
 `locales` パラメーターを省略すると、このメソッドの戻り値はコンピューター間で一致しないため、スクリプト用には適していません。  このシナリオでは、このメソッドは表示テキストの書式設定にのみ使用し、計算の一部としては使用しないでください。  
  
## 使用例  
 次の例は、ロケールと比較オプションを指定して `toLocaleTimeString` メソッドを使用する方法を示します。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` パラメーターと `options` パラメーター:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [toTimeString メソッド \(Date\)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString メソッド \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)