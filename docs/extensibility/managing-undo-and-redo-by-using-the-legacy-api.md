---
title: "元に戻したり、レガシ API を使用して再実行を管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c50316b7d5786b1fb3f07255eaf4d875f7f41e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>管理元に戻すと、レガシ API を使用して再実行
エディターでは、ユーザーがコードを変更するときに、最近の変更内容を反転できる元に戻す操作をサポートする必要があります。 ほとんどのエディターで実装[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]と[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]統合開発環境 (IDE) によって自動的に提供元に戻す機能を持つことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 元に戻す管理の実装](../extensibility/how-to-implement-undo-management.md)  
 エディターの 1 つまたは複数のビューで元に戻す機能を提供します。  
  
 [方法: 元に戻すスタックをクリアします](../extensibility/how-to-clear-the-undo-stack.md)  
 元に戻すスタックをクリアする方法について説明します。  
  
 [方法: リンクされた Undo 管理を使用](../extensibility/how-to-use-linked-undo-management.md)  
 エディターには、リンク元に戻す管理が組み込まれています。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 複数のビューをサポートしているのため元に戻す管理を提供します。  
  
## <a name="related-sections"></a>関連項目