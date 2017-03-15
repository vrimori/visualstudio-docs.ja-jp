---
title: "&#39;End SyncLock&#39; の前には、対応する &#39;SyncLock&#39; が必要です | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30674"
  - "bc30674"
helpviewer_keywords: 
  - "BC30674"
ms.assetid: 2d473b0b-ca9e-43b5-9bcb-b00766bc90a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End SyncLock&#39; の前には、対応する &#39;SyncLock&#39; が必要です
`SyncLock` ブロックは `SyncLock` キーワードから始まり `End` `SyncLock` コンストラクトで終了します。  
  
 **エラー ID:** BC30674  
  
### このエラーを解決するには  
  
-   `SyncLock` ブロックは必ず `SyncLock` ステートメントで始まるようにしてください。  
  
## 参照  
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)