---
title: "値引数の循環参照はサポートされていません。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 値引数の循環参照はサポートされていません。
無効な値で `JSON.stringify` を呼び出そうとしました。  `value` 引数 \(配列またはオブジェクト\) に循環参照が含まれています。  
  
### このエラーを解決するには  
  
-   引数から循環参照を削除します。  
  
## 使用例  
 この例のコードでは、`john` に `mary` への参照が指定され、`mary` に `john` への参照が指定されているため、ランタイム エラーが発生します。  循環参照を削除するには、`mary` オブジェクトのプロパティ `brother` または `john` オブジェクトの `sister` プロパティを削除または設定解除します。  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## 参照  
 [JSON オブジェクト](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript ランタイム エラー](../../javascript/reference/javascript-run-time-errors.md)