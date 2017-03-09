---
title: "例外のトラブルシューティング : System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException クラス"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Data.StrongTypingException
<xref:System.Data.StrongTypingException> は、厳密に型指定された <xref:System.DBNull> 内の <xref:System.Data.DataTable.DataSet%2A> 値にユーザーがアクセスすると発生します。  
  
## 関連するヒント  
 **StrongTypingException のエラー処理を追加します。**  
 <xref:System.Data.DataTable.DataSet%2A> にアクセスするコードを `Try…Catch` ブロック内に配置して <xref:System.Data.StrongTypingException> をキャッチします。  
  
## 参照  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)