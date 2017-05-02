---
title: "decodeURI 関数 (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI メソッド"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# decodeURI 関数 (JavaScript)
エンコード前の URI \(Uniform Resource Identifier\) を取得します。  
  
## 構文  
  
```  
decodeURI(URIstring)  
```  
  
## 解説  
 `URIstring` 引数は必須で、エンコードされた URI を表す値を指定します。  
  
 使用されていない `unescape` 関数の代わりには、`decodeURI` 関数を使用します。  
  
 `decodeURI` 関数は、文字列値を返します。  
  
 `URIString` が無効な場合は URIError が発生します。  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 使用例  
 次のコードでは、URI コンポーネントをエンコードしてからデコードしています。  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global オブジェクト](../../javascript/reference/global-object-javascript.md)