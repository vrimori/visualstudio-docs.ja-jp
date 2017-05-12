---
title: "localeCompare メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare メソッド"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# localeCompare メソッド (String) (JavaScript)
現在のロケールで 2 つの文字列が同等かどうかを判定します。  
  
## 構文  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## パラメーター  
 `stringVar`  
 Required.  比較する最初の文字列。  
  
 `stringExp`  
 Required.  比較する 2 番目の文字列。  
  
 `locales`  
 Optional.  1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。  複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。  このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  このパラメーターは、[BCP 47](http://tools.ietf.org/html/rfc5646) 標準に準拠している必要があります。詳細については、「[Intl.Collator オブジェクト](../../javascript/reference/intl-collator-object-javascript.md)」を参照してください。  
  
 `options`  
 省略可能。  比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。詳細については、「[Intl.Collator オブジェクト](../../javascript/reference/intl-collator-object-javascript.md)」を参照してください。  
  
## 解説  
 比較文字列の場合は、`String` オブジェクトまたは文字列リテラルを指定できます。  
  
 Internet Explorer 11 以降では、`localeCompare` は、`locales` パラメーターと `options` パラメーターのサポートを追加する `Intl.Collator` オブジェクトを内部的に使用して、比較を実行します。  これらのパラメーターの詳細については、「[Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)」および「[Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md)」を参照してください。  
  
> [!IMPORTANT]
>  `locales` パラメーターと `options` パラメーターは、一部のドキュメント モードとブラウザー バージョンではサポートされていません。  詳細については、「必要条件」を参照してください。  
  
 `localeCompare` メソッドでは、ロケールに基づいて `stringVar` と `stringExp` の文字列を比較し、システムの既定のロケールの並べ替え順序に従って、次のいずれかの結果を返します。  
  
-   `stringVar` が `stringExp` の前になる場合は \-1。  
  
-   `stringVar` が `stringExp` の後ろになる場合は \+1。  
  
-   2 つの文字列が等しい場合は 0 \(ゼロ\)。  
  
## 使用例  
 `localeCompare` の使用例を次のコードに示します。  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## 使用例  
 ドイツ語 \(ドイツ\) ロケールでの `localeCompare` の使用方法を次のコードに示します。  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## 使用例  
 次の例は、ドイツ語 \(ドイツ\) ロケールで、ドイツ語の電話帳の並べ替え順序を指定するロケール固有の拡張機能と共に `localeCompare` を使用する方法を示しています。  この例は、ロケール固有の違いを示しています。  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` パラメーターと `options` パラメーター:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [toLocaleString メソッド \(Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)