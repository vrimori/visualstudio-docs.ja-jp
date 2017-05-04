---
title: "endsWith メソッド (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# endsWith メソッド (String) (JavaScript)
文字列または部分文字列が別の指定された文字列で終了するかどうかを示す値を返します。  
  
## 構文  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### パラメーター  
 `stringObj`  
 必須です。  検索対象の文字列オブジェクト。  
  
 `str`  
 必須です。  検索文字列。  
  
 `position`  
 省略可能です。  文字列オブジェクトで検索する最初の文字の位置 \(0 で始まります\)。  
  
## 戻り値  
 `position` で始まる文字列が検索文字列で終了する場合、`endsWith` メソッドは `true` を返します。それ以外の場合は、`false` を返します。  
  
## 例外  
 `str` が `RegExp` の場合、`TypeError` がスローされます。  
  
## 解説  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]