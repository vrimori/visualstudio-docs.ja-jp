---
title: "未終了のコメントです。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 未終了のコメントです。
複数行コメント ブロックを開始しましたが、適切に終了していません。  複数行コメントは "\/\*" で開始し、これを逆にした "\*\/" で終了する必要があります。  次に例を示します。  
  
```javascript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### このエラーを解決するには  
  
-   複数行コメントは、必ず "\*\/" で終了するようにします。  
  
## 参照  
 [コメント ステートメント](../../javascript/reference/comment-statements-javascript.md)