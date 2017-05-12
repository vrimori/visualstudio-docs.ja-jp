---
title: "decodeURIComponent 関数 (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent メソッド"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# decodeURIComponent 関数 (JavaScript)
エンコード前の URI \(Uniform Resource Identifier\) コンポーネントを取得します。  
  
## 構文  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## 解説  
 `encodedURIString` 引数は必須で、エンコードされた URI コンポーネントを表す値を指定します。  
  
 URIComponent は完全な URI の一部です。  
  
 `encodedURIString` が無効な場合は URIError が発生します。  
  
## 使用例  
 次のコードでは、URI をエンコードしてからデコードします。  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)