---
title: ブレークポイント エラー |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b08b9bee82a2505411be95ef2e6634e7897c15ec
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153762"
---
# <a name="breakpoint-errors"></a>ブレークポイント エラー
次は、ブレークポイントがコードにバインドしようとしたときにプロセスを説明しますが、失敗します。  
  
## <a name="troubleshoot-a-breakpoint-error"></a>ブレークポイント エラーをトラブルシューティングします。  
  
1.  デバッグ エンジン (DE) を送信する[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)セッション デバッグ マネージャー (SDM)。  
  
2.  SDM コール[IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) エラーのブレークポイントを取得します。  
  
3.  SDM コール[IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)エラー ブレークポイントが元の保留中のブレークポイントを取得します。  
  
4.  SDM コール[IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)エラー ブレークポイントがバインドに失敗した理由を取得します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)