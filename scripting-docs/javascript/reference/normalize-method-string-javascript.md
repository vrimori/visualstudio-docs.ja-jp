---
title: "normalize メソッド (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# normalize メソッド (String) (JavaScript)
指定した文字列の Unicode 正規化形式を返します。  
  
## 構文  
  
```  
stringObj.normalize([form]);  
```  
  
#### パラメーター  
 `stringObj`  
 必須。  テスト対象の String オブジェクト。  
  
 `form`  
 省略可能です。  Unicode 正規化形式の値。  
  
## 戻り値  
 指定した文字列の Unicode 正規化形式。  
  
## 例外  
 `form` がサポートされていない値の場合は、`RangeError` がスローされます。  
  
## 解説  
 `stringObj` が文字列ではない場合、まず文字列に変換してから、メソッドは文字列の Unicode 正規化形式を返そうとします。  
  
 `form` は、[Unicode Standard Annex \#15](http://www.unicode.org/reports/tr15/) で指定されている値に対応する "NFC"、"NFD"、"NFKC"、"NFKD" のいずれかの Unicode 正規化形式の値でなければなりません。  `form` の既定値は "NFC" です。  
  
## 使用例  
 次のコード例は、`normalize` メソッドの使用法を示しています。  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]