---
title: "format プロパティ (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format プロパティ (Intl.DateTimeFormat)
指定された日時フォーマッタの設定を使用してロケール固有の日付の書式を設定する関数を返します。  
  
## 構文  
  
```  
dateTimeFormatObj.format  
```  
  
#### パラメーター  
 `dateTimeFormatObj`  
 必須。  フォーマッタとして使用する `DateTimeFormat` オブジェクトの名前。  
  
## 解説  
 `format` プロパティによって返される関数は、`date` という単一の引数を受け取り、`DateTimeFormat` オブジェクトで指定されたオプションを使用して、ローカライズされた日付を表す文字列を返します。  返される関数の `date` パラメーターは、数値、日付文字列、または `Date` オブジェクトである必要があります。  `date` を指定しない場合、この関数では既定の入力値として [Date.now](../../javascript/reference/date-now-function-javascript.md) が使用されます。  
  
## 使用例  
 次の例では、`DateTimeFormat` オブジェクトを使用して、日付 "Dec 1, 2007" をドイツ語にローカライズし、書式を再設定します。  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [Intl.DateTimeFormat オブジェクト](../../javascript/reference/intl-datetimeformat-object-javascript.md)