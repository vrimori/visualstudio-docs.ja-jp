---
title: "encodeURI 関数 (JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI メソッド"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURI 関数 (JavaScript)
テキストを有効な URI にエンコードします。  
  
## 構文  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## 解説  
 `URIString` 引数は必須で、エンコードされた URI を表す値を指定します。  
  
 `encodeURI` 関数はエンコードした URI を返します。  結果を `decodeURI` に渡すと、元の文字列が返されます。  `encodeURI` 関数は、「:」、「\/」、「;」、「?」の各文字はエンコードしません。  これらの文字をエンコードする場合は、`encodeURIComponent` を使用します。  
  
## 使用例  
 次のコードでは、URI をエンコードしてからデコードします。  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)