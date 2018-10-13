---
title: ブレークポイント エラー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 136b371b6d024a93e2a4cb4cadd792928db49800
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197967"
---
# <a name="breakpoint-errors"></a>ブレークポイント エラー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

次のブレークポイントがコードにバインドしようとしたときにプロセスを説明しますは失敗します。  
  
## <a name="troubleshooting-a-breakpoint-error"></a>ブレークポイント エラーのトラブルシューティング  
  
1.  デバッグ エンジン (DE) を送信する[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)セッション デバッグ マネージャー (SDM)。  
  
2.  SDM コール[IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) エラーのブレークポイントを取得します。  
  
3.  SDM コール[IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)エラー ブレークポイントが元の保留中のブレークポイントを取得します。  
  
4.  SDM コール[IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)エラー ブレークポイントがバインドに失敗した理由を取得します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

