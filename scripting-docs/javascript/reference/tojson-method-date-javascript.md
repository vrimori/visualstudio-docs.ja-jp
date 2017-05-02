---
title: "toJSON メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "toJSON メソッド"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# toJSON メソッド (Date) (JavaScript)
[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) メソッドで使用され、オブジェクトのデータを JSON \(JavaScript Object Notation\) シリアル化できます。  
  
## 構文  
  
```  
  
objectname.toJSON()  
```  
  
## パラメーター  
 `objectname`  
 必須です。  JSON シリアル化を行うオブジェクトを指定します。  
  
## 解説  
 `toJSON` メソッドは、`JSON.stringify` 関数によって使用されます。  `JSON.stringify` は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値を JSON テキストに シリアル化します。  `JSON.stringify` で `toJSON` メソッドを使用できる場合は、`JSON.stringify` が呼び出されたときに `toJSON` メソッドが呼び出されます。  
  
 `toJSON` メソッドは、[Date](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトの組み込みメンバーです。  これは、サフィックス Z で示される UTC のタイム ゾーンの ISO 形式の日付文字列を返します。  
  
 `Date` 型の `toJSON` メソッドをオーバーライドするか、または他のオブジェクト型に対して `toJSON` メソッドを定義すると、JSON シリアル化の前に特定のオブジェクト型のデータを変換できます。  
  
## 使用例  
 `toJSON` メソッドを使用して、文字列のメンバー値を大文字でシリアル化する例を次に示します。  `toJSON` メソッドは、`JSON.stringify` メソッドが呼び出されるときに呼び出されます。  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## 使用例  
 [Date](../../javascript/reference/date-object-javascript.md) オブジェクトの組み込みメンバーである `toJSON` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## 必要条件  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  **対象:**  [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [JSON オブジェクト](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify 関数](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)