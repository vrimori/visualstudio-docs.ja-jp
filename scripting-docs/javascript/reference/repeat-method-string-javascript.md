---
title: "repeat メソッド (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# repeat メソッド (String) (JavaScript)
元の文字列を指定した回数繰り返したものと同等の値を持つ、新しい文字列オブジェクトを返します。  
  
## 構文  
  
```  
stringObj.repeat(count);  
```  
  
#### パラメーター  
 `stringObj`  
 必須です。  String オブジェクト  
  
 `count`  
 必須です。  返される文字列内で、元の文字列を繰り返す回数。  
  
## 例外  
 このメソッドは、引数が負の値または \+ Infinity の場合にのみ、RangeError をスローします。  
  
## 解説  
 `repeat` メソッドは、`count` で指定された回数、元の文字列を新しい文字列に連結します。  
  
 このメソッドは、`count` が `Infinity` より小さい正の数ではない場合にエラーをスローします。  
  
## 使用例  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]