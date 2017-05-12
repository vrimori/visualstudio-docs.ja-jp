---
title: "関数が必要です | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 関数が必要です
`Function` オブジェクトではないオブジェクトに対して Function プロトタイプのいずれかのメソッドを呼び出そうとしたか、関数呼び出しのコンテキストでオブジェクトを使用しました。  たとえば、次のコードは **example** が関数ではないのでエラーが発生します。  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### このエラーを解決するには  
  
-   Function プロトタイプのメソッドは、`Function` オブジェクトのみに対して呼び出します。  
  
-   関数呼び出し演算子 \(`()`\) は、関数を呼び出す場合にのみ使用します。  
  
## 参照  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [prototype プロパティ \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)