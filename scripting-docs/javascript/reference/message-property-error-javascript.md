---
title: "message プロパティ (Error) (JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message プロパティ"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# message プロパティ (Error) (JavaScript)
エラー メッセージの文字列を返します。  
  
## 構文  
  
```  
  
errorObj.message  
```  
  
## パラメーター  
 `errorObj`  
 必須です。  `Error` オブジェクトのインスタンスを指定します。  
  
## 解説  
 `message` プロパティは、特定のエラーに関連付けられているエラー メッセージを格納する文字列を返します。  
  
 `description` プロパティと `message` プロパティは、同じ機能を提供します。  `description` プロパティは下位互換性を提供し、`message` プロパティは ECMA 規格に準拠します。  
  
## 使用例  
 TypeError 例外をスローし、エラーの名前およびそのメッセージを表示する例を次に示します。  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## 使用例  
 このコードによって、次のような出力が生成されます。  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **対象**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## 参照  
 [description プロパティ \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [name プロパティ \(Error\)](../../javascript/reference/name-property-error-javascript.md)