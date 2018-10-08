---
title: ブレークポイントのヒット |Microsoft Docs
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
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 394ff3ba3826240df43faea4acd4aee107de1969
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545668"
---
# <a name="hitting-a-breakpoint"></a>ブレークポイントのヒット
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ブレークポイントのヒット](https://docs.microsoft.com/visualstudio/extensibility/debugger/hitting-a-breakpoint)します。  
  
次に示します (DE) デバッグ エンジンが実行されている、またはステップ実行中にブレークポイントをヒットしたときのプロセスを。  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>ブレークポイントをヒットのトラブルシューティング  
  
1.  DE 送信、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)インターフェイスとして、 **EVENT_SYNC_STOP**します。  
  
2.  セッション デバッグ マネージャー (SDM) を呼び出す[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)ヒットしたブレークポイントを取得します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

