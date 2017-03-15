---
title: "例外のトラブルシューティング : System.Threading.SynchronizationLockException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SynchronizationLockException 例外"
  - "System.Threading.SynchronizationLockException 例外"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Threading.SynchronizationLockException
この例外は、メソッドで、特定の `Monitor` に関するロックを呼び出し元で所有する必要がある場合に、そのロックを所有していない呼び出し元がメソッドを呼び出すとスローされます。  
  
## コメント  
 <xref:System.Threading.SynchronizationLockException> は、<xref:System.Threading.Monitor.Exit%2A> クラスの <xref:System.Threading.Monitor.Pulse%2A>、<xref:System.Threading.Monitor.PulseAll%2A>、<xref:System.Threading.Monitor.Wait%2A>、および `Monitor` の各メソッドを、同期されていないコードのブロックから呼び出すとスローされます。  
  
## 参照  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)