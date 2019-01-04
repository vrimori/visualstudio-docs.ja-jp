---
title: ブレークポイントのヒット |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 728258dc363f906e005c654909cb86fd782824a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935633"
---
# <a name="hit-a-breakpoint"></a>ブレークポイントに到達する
次のセクションでは、デバッグ エンジン (DE) を実行している、またはステップ実行中にブレークポイントに達すると、プロセスが説明します。  
  
## <a name="troubleshoot-a-hit-breakpoint"></a>ブレークポイントをヒットのトラブルシューティングします。  
  
1.  DE 送信、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)インターフェイスとして、 **EVENT_SYNC_STOP**します。  
  
2.  セッション デバッグ マネージャー (SDM) を呼び出す[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)ヒットしたブレークポイントを取得します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントを呼び出す](../../extensibility/debugger/calling-debugger-events.md)