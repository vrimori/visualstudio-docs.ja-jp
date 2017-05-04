---
title: "catch が必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# catch が必要です。
例外処理の **try** ブロックを使用しましたが、対応する **catch** ステートメントが記述されていません。  例外処理機構には、失敗する可能性があるコードおよび例外が発生した場合に実行すべきではないコードを **try**  ブロックでラップして記述する必要があります。  例外は **throw** ステートメントを使用して **try** ブロックの内部からスローされ、**try** ブロックの外部の 1 つ以上の **catch** ステートメントでキャッチされます。  
  
### このエラーを解決するには  
  
-   対応する **catch** ブロックを追加します。  
  
-   **catch** ブロックの代わりに **finally** ブロックを使用してみます。  
  
## 参照  
 [try...catch...finally ステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)