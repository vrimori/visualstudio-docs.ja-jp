---
title: 元に戻したり、レガシ API を使用して再実行の管理 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bb1cc883941c8365e4d4341c93084beaef44d48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545092"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>管理元に戻すと、レガシ API を使用して再実行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[管理を元に戻すと、レガシ API を使用して再実行](https://docs.microsoft.com/visualstudio/extensibility/managing-undo-and-redo-by-using-the-legacy-api)します。  
  
エディターでは、ユーザーがコードを変更するときに、最近の変更内容を反転できるように元に戻す操作をサポートする必要があります。 ほとんどのエディターでは実装[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]統合開発環境 (IDE) によって自動的に提供元に戻す機能を持つことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 元に戻すの管理を実装する](../extensibility/how-to-implement-undo-management.md)  
 エディターの 1 つまたは複数のビューで元に戻す機能を提供します。  
  
 [方法: 元に戻すスタックをクリアする](../extensibility/how-to-clear-the-undo-stack.md)  
 元に戻すスタックをクリアする方法について説明します。  
  
 [方法: リンクされた元に戻すの管理を使用する](../extensibility/how-to-use-linked-undo-management.md)  
 エディターには、リンク元に戻す管理が組み込まれています。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 複数のビューをサポートしているのため元に戻す管理を提供します。  
  
## <a name="related-sections"></a>関連項目

