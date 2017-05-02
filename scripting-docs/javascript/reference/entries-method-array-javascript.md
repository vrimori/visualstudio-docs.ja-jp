---
title: "entries メソッド (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9bc46afb-74d2-4f99-8c95-f46475acf21d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# entries メソッド (Array) (JavaScript)
配列のキーと値のペアを返す反復子を返します。  
  
## 構文  
  
```  
arrayObj.entries();  
```  
  
#### パラメーター  
 `arrayObj`  
 必須です。  Array オブジェクト。  
  
## 解説  
  
## 使用例  
 次の例では、配列のキーと値のペアを取得する方法を示します。  
  
```javascript  
var entries = ["a", "b", "c"].entries();  
// entries.next().value == [0, "a"]  
// entries.next().value == [1, "b"]  
// entries.next().value == [2, "c"]   
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]