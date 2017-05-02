---
title: "Enumerator オブジェクトが必要です。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Enumerator オブジェクトが必要です。
`Enumerator` 以外の型のオブジェクトに対して、**Enumerator.prototype.atEnd、Enumerator.prototype.item、Enumerator.prototype.moveFirst**、または **Enumerator.prototype.moveNext** の各メソッドを呼び出そうとしました。  この種類の呼び出しに対するオブジェクトは、`Enumerator` 型にする必要があります。  この規則に違反するコードの例を次に示します。  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### このエラーを解決するには  
  
-   `Enumerator` 型のオブジェクトには、**Enumerator.prototype.atEnd** メソッド、**Enumerator.prototype.item** メソッド、**Enumerator.prototype.moveFirst** メソッド、または **Enumerator.prototype.moveNext** メソッドのみを呼び出します。  オブジェクトが `Enumerator` オブジェクトかどうかを確認するには、次のコードを使用します。  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## 参照  
 [Enumerator オブジェクト](../../javascript/reference/enumerator-object-javascript.md)