---
title: ブレークポイントの削除 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: b63fa7622b7dea4a6ad5c516547518911110a8ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958041"
---
# <a name="deleting-a-breakpoint"></a>ブレークポイントの削除
次に示します保留中のブレークポイントを削除するときのプロセスを。  
  
## <a name="deletion-process"></a>削除プロセス  
 セッション デバッグ マネージャー (SDM) を呼び出す、 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)から保留中のブレークポイントとバインドされたすべてのブレークポイントを削除するメソッドにバインドされています。  
  
> [!NOTE]
>  呼び出して 1 つのバインドされたブレークポイントを削除することも[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントを呼び出す](../../extensibility/debugger/calling-debugger-events.md)