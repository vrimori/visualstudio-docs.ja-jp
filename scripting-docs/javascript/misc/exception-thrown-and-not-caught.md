---
title: "例外の値がスローされ、キャッチされませんでした。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 例外の値がスローされ、キャッチされませんでした。
コードに `throw` ステートメントを記述しましたが、**try** ブロックで囲まなかったか、またはエラーをトラップするための対応する **catch** ブロックがありません。  例外は **throw** ステートメントを使用して **try** ブロックの内部からスローされ、**try** ブロックの外部の **catch**ステートメントでキャッチされます。  
  
### このエラーを解決するには  
  
-   例外をスローできるコードを **try** ブロックで囲み、対応する **catch** ブロックを必ず記述してください。  
  
-   catch ステートメントが正しい形式の例外を受け取るようにしてください。  
  
-   例外が再びスローされる場合のために、別の対応する catch ステートメントがあることを確認します。  
  
## 参照  
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)   
 [throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally ステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)