---
title: "Intl.NumberFormat オブジェクト (JavaScript) | Microsoft Docs"
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
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Intl.NumberFormat オブジェクト (JavaScript)
ロケール固有の数値の書式設定を提供します。  
  
## 構文  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### パラメーター  
 `numberFormatObj`  
 必須。  `NumberFormat` オブジェクトを代入する変数名を指定します。  
  
 `locales`  
 省略可能。  1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。  複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。  このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  詳細については、次の「解説」を参照してください。  
  
 `options`  
 省略可能。  数値書式設定オプションを指定する 1 つ以上のプロパティを含むオブジェクト。  詳細については、「解説」を参照してください。  
  
## 解説  
 `locales` パラメーターは、[BCP 47](http://tools.ietf.org/html/rfc5646) の言語またはロケールのタグ \("en\-US" や "zh\-CN" など\) に準拠している必要があります。  タグには、言語、地域、国、バリエーションを含めることができます。  言語タグの例については、BCP 47 の[付録 A](http://tools.ietf.org/html/rfc5646#appendix-A) を参照してください。  `NumberFormat` では、\-nu の後に **\-u** サブタグを追加して、番号付けシステム拡張機能を指定できます。  
  
 "*language*\-*region*\-u\-nu\-*numberingsystem*"  
  
 *numberingsystem* には、arab、arabext、bali、beng、deva、fullwide、gujr、guru、hanidec、khmr、knda、laoo、latn、limb、mylm、mong、mymr、orya、tamldec、telu、thai、tibt のいずれかを指定します。  
  
 `options` パラメーターには、次のプロパティを含めることができます。  
  
|Property|Description|使用可能な値|既定値|  
|--------------|-----------------|------------|---------|  
|`localeMatcher`|使用するロケール照合アルゴリズムを指定します。|"lookup" および "best fit"|"best fit"|  
|`style`|数値書式スタイルを指定します。|"decimal"、"percent"、および "currency"|"decimal"|  
|`currency`|ISO 4217 通貨値を英字コードで指定します。  `style` が "currency" に設定されている場合は、この値が必要です。|ISO の[通貨コード一覧](http://www.currency-iso.org/en/home/tables/table-a1.html) を参照してください。|未定義|  
|`currencyDisplay`|通貨を ISO 4217 の英字の通貨コードで表示するか、ローカライズされた通貨記号で表示するか、ローカライズされた通貨名で表示するかを指定します。  この値は、`style` が "currency" に設定されている場合にのみ使用されます。|"code"、"symbol"、および "name"|"symbol"|  
|`useGrouping`|桁区切り記号を使用するかどうかを指定します。|true、false|`true`.|  
|`minimumIntegerDigits`|使用する整数部の最小桁数を指定します。|1 ～ 21。|21|  
|`minimumFractionDigits`|.  使用する小数部の最小桁数を指定します。|0 ～ 20。|0|  
|`maximumFractionDigits`|使用する小数部の最大桁数を指定します。|この値の範囲は `minimumFractionDigits` ～ 20 です。|20.|  
|`minimumSignificantDigits`|表示する小数部の最小桁数を指定します。|この値の範囲は 1 ～ 21 です。|1|  
|`maximumSignificantDigits`|表示する小数部の最大桁数を指定します。|この値の範囲は `minimumSignificantDigits` ～ 21 です。|21|  
  
## Properties  
 `NumberFormat` オブジェクトのプロパティを次の表に示します。  
  
|||  
|-|-|  
|プロパティ|説明|  
|[constructor](../../javascript/reference/constructor-property-intl-numberformat.md)|数値フォーマッタ オブジェクトを作成する関数を指定します。|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|数値フォーマッタの設定を使用して数値の書式を設定する関数を返します。|  
|[prototype](../../javascript/reference/prototype-property-intl-numberformat.md)|数値フォーマッタのプロトタイプへの参照を返します。|  
  
## メソッド  
 `NumberFormat` オブジェクトのメソッドを次の表に示します。  
  
|||  
|-|-|  
|メソッド|説明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|数値フォーマッタ オブジェクトのプロパティと値を含むオブジェクトを返します。|  
  
## 使用例  
 次の例では、書式オプションを指定して en\-US ロケールの `NumberFormat` オブジェクトを作成します。  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## 使用例  
 次の例は、いくつかの異なるロケールとオプションを使用した結果を示しています。  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator オブジェクト](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat オブジェクト](../../javascript/reference/intl-datetimeformat-object-javascript.md)