---
title: "JavaScript ランタイム エラー | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT-32725"
  - "VS.WebClient.Help.SCRIPT7002"
  - "VS.WebClient.Help.SCRIPT1001"
  - "VS.WebClient.Help.SCRIPT16389"
  - "VS.WebClient.HelpSCRIPT50"
  - "VS.WebClient.HelpSCRIPT70"
  - "VS.WebClient.HelpSCRIPT87"
  - "VS.WebClient.HelpSCRIPT65535"
  - "VS.WebClient.HelpSCRIPT445"
  - "VS.WebClient.HelpSCRIPT600"
  - "VS.WebClient.HelpSCRIPT2343"
  - "VS.WebClient.HelpSCRIPT122"
  - "VS.WebClient.HelpSCRIPT28"
  - "VS.WebClient.HelpSCRIPT16386"
  - "VS.WebClient.HelpSCRIPT7015"
  - "VS.WebClient.HelpSCRIPT3"
  - "VS.WebClient.HelpSCRIPT16388"
  - "VS.WebClient.HelpSCRIPT14"
  - "VS.WebClient.HelpSCRIPT12030"
  - "VS.WebClient.HelpSCRIPT12029"
  - "VS.WebClient.HelpSCRIPT1001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "エラー [JavaScript]"
  - "ランタイム エラー, JavaScript"
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# JavaScript ランタイム エラー
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ランタイム エラーは、システムでは実行できないアクションを、スクリプトが実行しようとしたときに発生するエラーです。 ランタイム エラーは、可変式を評価しているときやメモリを割り当てているときに発生することがあります。  
  
## Windows ランタイム エラー  
 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリで Windows ランタイム API を使用している場合、Windows ランタイムの HRESULT から変換された JavaScript エラーが発生する場合があります。 下位ビットの 16 進数値を取得して 10 進数に変換することによって、0x80070000 の範囲にある Windows ランタイムの HRESULT が JavaScript エラーに変換されます。 たとえば、HRESULT 0x80070032 は 10 進数値 50 に変換され、JavaScript エラーは SCRIPT50 となります。 HRESULT 0x80074005 は 10 進数値 16389 に変換され、JavaScript エラーは SCRIPT16389 となります。  
  
## エラー  
  
|エラー番号|説明|  
|-----------|--------|  
|5|[アクセスが拒否されました](../../javascript/misc/access-is-denied.md)|  
|438|[オブジェクトは、このプロパティまたはメソッドをサポートしていません。](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|メモリ不足|  
|5029|[配列の長さは、有限の正の整数でなければなりません。](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[配列の長さは、割り当てられた有限の正数でなければなりません。](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[配列または引数のオブジェクトが必要です。](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[ブール値が必要です。](../../javascript/misc/boolean-expected.md)|  
|5003|[関数の結果に割り当てられません。](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|['this' に割り当てることはできません。](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[value 引数の循環参照はサポートされません。](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[データ オブジェクトが必要です。](../../javascript/misc/date-object-expected.md)|  
|5015|[列挙子オブジェクトが必要です。](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[例外がスローされ、キャッチされませんでした。](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[正規表現の中に '\)' が必要です。](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[正規表現の中に '&#93;' が必要です。](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[関数には、有効なプロトタイプ オブジェクトが存在しません。](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[関数が必要です。](../../javascript/misc/function-expected.md)|  
|5008|[無効な代入です。](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[文字セットの範囲が無効です。](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[置換関数の引数が無効です。](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[JavaScript オブジェクトが必要です。](../../javascript/misc/javascript-object-expected.md)|  
|5001|[数字が必要です。](../../javascript/misc/number-expected.md)|  
|5007|[オブジェクトが必要です。](../../javascript/misc/object-expected.md)|  
|5012|[オブジェクトのメンバが必要です。](../../javascript/misc/object-member-expected.md)|  
|5016|[正規表現オブジェクトが必要です。](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[文字列が必要です。](../../javascript/misc/string-expected.md)|  
|5017|[正規表現で構文エラーが発生しました。](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[小数の桁数が有効範囲を超えています。](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[有効桁数の範囲を超えています。](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[デコードする URI は正しくエンコードされていません。](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[エンコードする URI は無効な文字を含んでいます。](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[未定義の識別子です。](../../javascript/misc/undefined-identifier.md)|  
|5018|[予期しない量指定子です。](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[VBArray が必要です。](../../javascript/misc/vbarray-expected.md)|  
  
## 参照  
 [JavaScript 構文エラー](../../javascript/reference/javascript-syntax-errors.md)