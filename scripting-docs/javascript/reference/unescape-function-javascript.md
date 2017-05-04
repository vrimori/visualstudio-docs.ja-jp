---
title: "unescape 関数 (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape メソッド"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# unescape 関数 (JavaScript)
`escape` 関数を使ってエンコードされた `String` オブジェクトの文字列をデコードします。  使用しないでください。  
  
## 構文  
  
```  
unescape(charString)   
```  
  
## 解説  
 必須の `charString` 引数は、デコードする `String` オブジェクトまたはリテラルです。  
  
 `charstring` 関数は、`unescape` のコンテンツを文字列値として返します。  16 進の %*xx* 形式でエンコードされたすべての文字は、ASCII 文字セットの対応する文字に置き換えられます。  
  
 **%u** *xxxx* 形式 \(Unicode 文字\) にエンコードされた文字は、Unicode 文字に置き換えられます。その際、*xxxx* は 16 進数に変換されます。  
  
> [!NOTE]
>  `unescape` 関数を URI \(Uniform Resource Identifier\) のデコードに使用しないでください。  代わりに、`decodeURI` 関数または `decodeURIComponent` 関数の使用をお勧めします。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 参照  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape 関数](../../javascript/reference/escape-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)