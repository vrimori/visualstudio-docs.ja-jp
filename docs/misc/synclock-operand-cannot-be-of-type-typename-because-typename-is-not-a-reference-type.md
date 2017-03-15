---
title: "&#39;&lt;typename&gt;&#39; は参照型ではないので、&#39;SyncLock&#39; オペランドを型 &#39;&lt;typename&gt;&#39; にすることはできません | Microsoft Docs"
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
  - "vbc30582"
  - "bc30582"
helpviewer_keywords: 
  - "BC30582"
ms.assetid: 953aecf2-629a-4272-94bd-abf88f785e63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; は参照型ではないので、&#39;SyncLock&#39; オペランドを型 &#39;&lt;typename&gt;&#39; にすることはできません
`SyncLock` ステートメントでは、複数のスレッドが同時に同じステートメントを実行しないようにすることによって、1 つの式で複数のステートメントを同期できます。`SyncLock` ステートメント内の式の型は、クラス、モジュール、インターフェイス、配列、またはデリゲートなどの参照型である必要があります。  
  
 **エラー ID:** BC30582  
  
### このエラーを解決するには  
  
-   型を適切な参照型に変更します。  
  
## 参照  
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)   
 [ビルド内にありません: Visual Basic でのマルチスレッド](http://msdn.microsoft.com/ja-jp/c731a50c-09c1-4468-9646-54c86b75d269)