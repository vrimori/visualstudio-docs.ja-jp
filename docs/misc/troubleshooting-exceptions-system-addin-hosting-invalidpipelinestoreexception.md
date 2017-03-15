---
title: "例外のトラブルシューティング : System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "InvalidPipelineStoreException 例外"
  - "System.AddIn.Hosting.InvalidPipelineStoreException 例外"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.AddIn.Hosting.InvalidPipelineStoreException
<xref:System.AddIn.Hosting.InvalidPipelineStoreException> 例外は、ディレクトリが見つからず、パイプライン ルート パスまたはアドイン パスにアクセスするためのアクセス許可がユーザーにない場合にスローされます。  
  
## コメント  
 <xref:System.IO.DirectoryNotFoundException> とは異なり、この例外ではパス情報が提供されません。 これにより、悪意のあるユーザーが間違ったパスを意図的に指定し、実際のパスを判断するために例外によって返される情報を利用することはできなくなります。  
  
 この例外は、アドインとパイプライン情報のストアをビルドおよび更新する <xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>、<xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>、<xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>、<xref:System.AddIn.Hosting.AddInStore.Update%2A>、および <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A> の各探索メソッドによってスローされます。  
  
## 参照  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)