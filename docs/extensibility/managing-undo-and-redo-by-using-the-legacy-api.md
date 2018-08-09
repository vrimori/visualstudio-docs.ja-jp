---
title: 元に戻したり、レガシ API を使用して再実行の管理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be60b3f0dd45a40663770b4b0debe8023e277f32
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638073"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>元に戻すを管理し、従来の API を使用して再実行
エディターでは、ユーザーがコードを変更するときに、最近の変更内容を反転できるように元に戻す操作をサポートする必要があります。 ほとんどのエディターでは実装[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]統合開発環境 (IDE) によって自動的に提供元に戻す機能を持つことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)  
 エディターの 1 つまたは複数のビューで元に戻す機能を提供します。  
  
 [方法: 元に戻すスタックをクリア](../extensibility/how-to-clear-the-undo-stack.md)  
 元に戻すスタックをクリアする方法について説明します。  
  
 [方法: リンクされた undo 管理の使用](../extensibility/how-to-use-linked-undo-management.md)  
 エディターには、リンク元に戻す管理が組み込まれています。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 複数のビューをサポートしているのため元に戻す管理を提供します。  
