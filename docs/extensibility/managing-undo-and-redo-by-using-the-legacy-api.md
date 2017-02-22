---
title: "管理の元に戻す/やり直しレガシ API を使用して | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] の従来の管理を元に戻す"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 管理の元に戻す/やり直しレガシ API を使用して
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターでは、ユーザーがこれらのコードを変更するときに、最近の変更内容を反転できるように元に戻す操作をサポートする必要があります。 ほとんどのエディターでは実装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 取り消しのサポートが統合開発環境 \(IDE\) によって自動的に提供されることができます。  
  
## このセクションの内容  
 [方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)  
 1 つまたは複数のビューのエディターで元に戻す機能を提供します。  
  
 [方法: 元に戻すスタックをクリアします](../extensibility/how-to-clear-the-undo-stack.md)  
 元に戻すスタックをクリアする方法について説明します。  
  
 [方法: リンクされた Undo 管理を使用](../extensibility/how-to-use-linked-undo-management.md)  
 エディターには、リンクされた undo 管理が組み込まれています。  
  
## 関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 複数のビューをサポートするエディターの元に戻す管理を提供します。  
  
## 関連項目