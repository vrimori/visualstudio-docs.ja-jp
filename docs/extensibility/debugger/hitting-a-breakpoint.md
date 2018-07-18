---
title: ブレークポイントにヒット |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f4788f8a038a274d6d94b4edf368e30ef495665
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109143"
---
# <a name="hitting-a-breakpoint"></a>ブレークポイントにヒット
次に示しますデバッグ エンジン (DE) を実行しているか、ステップ実行中にブレークポイントにヒット時のプロセスを。  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>ブレークポイントをヒットのトラブルシューティング  
  
1.  DE 送信、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)インターフェイスとして、 **EVENT_SYNC_STOP**です。  
  
2.  セッションのデバッグ マネージャー (SDM) を呼び出す[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)ヒットしたブレークポイントを取得します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)