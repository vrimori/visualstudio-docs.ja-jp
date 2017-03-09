---
title: "例外のトラブルシューティング : System.Windows.Xps.XpsWriterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException 例外"
  - "XpsWriterException 例外"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Windows.Xps.XpsWriterException
<xref:System.Windows.Xps.XpsWriterException> 例外は、<xref:System.Windows.Xps.XpsDocumentWriter> オブジェクトまたは <xref:System.Windows.Xps.VisualsToXpsDocument> オブジェクトの現在の状態と互換性がないオブジェクトのメソッドが呼び出された場合にスローされます。  
  
## コメント  
 たとえば、この例外は、いずれかの種類のオブジェクトが非同期書き込み操作を実行していないときに、そのオブジェクトの `CancelAsync` メソッドが呼び出された場合にスローされます。  
  
## 参照  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)