---
title: "例外のトラブルシューティング : System.DuplicateWaitObjectException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DuplicateWaitObjectException クラス"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.DuplicateWaitObjectException
<xref:System.DuplicateWaitObjectException> または <xref:System.Threading.WaitHandle> に渡された <xref:System.Threading.WaitHandle.WaitAll%2A> オブジェクトの配列が重複するオペレーティング システム処理を含む場合、<xref:System.Threading.WaitHandle.WaitAny%2A> 例外がスローされます。  
  
## 関連するヒント  
 **WaitAll または WaitAny に渡された WaitHandle オブジェクトが一意であることを確認します。**  
 <xref:System.Threading.WaitHandle> 配列には、同じオブジェクトへの複数の参照を含むことはできません。  
  
### コメント  
 共通言語ランタイム \(CLR : Common Language Runtime\) には、<xref:System.Threading.WaitHandle> オブジェクトの配列で実行を待機する同期オブジェクトに基づいたスレッド同期機構が用意されています。  
  
## 参照  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)