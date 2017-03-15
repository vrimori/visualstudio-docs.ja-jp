---
title: "例外のトラブルシューティング : System.IO.InternalBufferOverflowException | Microsoft Docs"
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
  - "InternalBufferOverflowException クラス"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IO.InternalBufferOverflowException
内部バッファーがオーバーフローすると、<xref:System.IO.InternalBufferOverflowException> 例外がスローされます。  
  
## 関連するヒント  
 **FileSystemWatcher を使用するとき、不要な変更通知をフィルターで除きます。**  
 FileSystemWatcher の使用時にファイルの変更が通知されると、コンポーネントが生成し、アプリケーション プログラミング インターフェイス \(API\) に渡すバッファーにそれらの変更が格納されます。 短時間に多数の変更が行われると、バッファーがオーバーフローし、その結果、<xref:System.IO.InternalBufferOverflowException> 例外が生成され、すべての変更が失われることがあります。 バッファーのオーバーフローを防止するには、<xref:System.IO.FileSystemWatcher.NotifyFilter%2A> プロパティと <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A> プロパティを使用して、不要な変更通知をフィルター処理します。 詳細については、「<xref:System.IO.FileSystemWatcher>」を参照してください。  
  
## コメント  
 <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A> プロパティを使用して内部バッファーのサイズを増やすこともできます。 ただし、バッファーのサイズを増やすとパフォーマンスに影響します。バッファーのサイズは、できるだけ小さくしておくことをお勧めします。  
  
## 参照  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)