---
title: "ブレークポイントの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1667da0798bba298fdead26105178905c0b9a9e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deleting-a-breakpoint"></a>ブレークポイントの削除
次のプロセスについて説明します、保留中のブレークポイントを削除するときに。  
  
## <a name="deletion-process"></a>削除プロセス  
 セッションのデバッグ マネージャー (SDM) を呼び出す、 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)からバインドされた保留中のブレークポイントとバインドされたすべてのブレークポイントを削除するメソッド。  
  
> [!NOTE]
>  呼び出しによって単一のバインドされたブレークポイントを削除することも[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)です。  
  
## <a name="see-also"></a>参照  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)