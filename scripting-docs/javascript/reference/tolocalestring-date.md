---
title: "toLocaleString (Date) | Microsoft Docs"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
現在のロケールまたは指定されたロケールでの既定の書式を使用して、日付データを文字列に変換します。  
  
## 構文  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### パラメーター  
 `dateObj`  
 Required.  変換対象の `Date` オブジェクト。  
  
 `locales`  
 省略可能。  1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。  複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。  このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  
  
 `options`  
 省略可能。  比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。  
  
## 解説  
 Internet Explorer 11 以降では、`toLocaleString` は、`locales` パラメーターと `options` パラメーターのサポートを追加する `Intl.DateTimeFormat` を内部的に使用して、比較を実行します。  これらのパラメーターの詳細については、「[Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)」を参照してください。  
  
> [!IMPORTANT]
>  `locales` パラメーターと `options` パラメーターは、一部のドキュメント モードとブラウザー バージョンではサポートされていません。  詳細については、「必要条件」を参照してください。  
  
 Internet Explorer 10 標準ドキュメント モード、以前のドキュメント モード、および互換捻出モードで `toLocaleString` を使用すると、次のようになります。  
  
-   現在のロケールの長い既定形式に日付データを変換し、`String` オブジェクトに格納したものが返されます。  
  
-   西暦 1601 から 1999 年の場合、日付はユーザーのコントロール パネルの地域設定に基づいた形式になります。  
  
> [!NOTE]
>  `locales` パラメーターを省略する場合、`toLocaleString` はユーザーに結果を表示する目的だけで使用してください。この関数の結果はコンピューターによって異なるため、スクリプト内で値を計算する目的では使用しないでください。  
  
## 使用例  
 `toLocaleString` メソッドを使用する方法の例を次に示します。  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## 使用例  
 次の例は、ロケールと比較オプションを指定して `toLocaleString` メソッドを使用する方法を示します。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` パラメーターと `options` パラメーター:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [toLocaleDateString メソッド \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)