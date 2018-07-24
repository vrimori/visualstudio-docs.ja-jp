---
title: ブレークポイントの削除 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc85104ca02922c1a28152d75550a821598d7b1e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203866"
---
# <a name="deleting-a-breakpoint"></a>ブレークポイントの削除
次に示します保留中のブレークポイントを削除するときのプロセスを。  
  
## <a name="deletion-process"></a>削除プロセス  
 セッション デバッグ マネージャー (SDM) を呼び出す、 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)から保留中のブレークポイントとバインドされたすべてのブレークポイントを削除するメソッドにバインドされています。  
  
> [!NOTE]
>  呼び出して 1 つのバインドされたブレークポイントを削除することも[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントを呼び出す](../../extensibility/debugger/calling-debugger-events.md)