---
title: "encodeURIComponent 関数 (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent メソッド"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURIComponent 関数 (JavaScript)
文字列を有効な URI \(Uniform Resource Identifier\) にエンコードします。  
  
## 構文  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## 解説  
 `encodedURIString` 引数は必須で、エンコードされた URI コンポーネントを表す値を指定します。  
  
 `encodeURIComponent` 関数はエンコードした URI を返します。  結果を `decodeURIComponent` に渡すと、元の文字列が返されます。  `encodeURIComponent` 関数では、すべての文字がエンコードされるので、\/folder1\/folder2\/default.html などのパスを表す文字列には注意が必要です。  スラッシュ \(\/\) もエンコードされるので、Web サーバーへの要求として送信する場合は無効になります。  文字列に URI コンポーネントが複数含まれる場合は、`encodeURI` 関数を使用します。  
  
## 使用例  
 次のコードでは、URI コンポーネントをエンコードしてからデコードしています。  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)