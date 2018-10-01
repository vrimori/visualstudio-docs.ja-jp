---
title: 中断モードでのステップ実行 |Microsoft Docs
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
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0721dcfe857f5c21aab634d02c29e864870c440b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539186"
---
# <a name="stepping-in-break-mode"></a>中断モードへのステップイン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[中断モードでのステップ実行](https://docs.microsoft.com/visualstudio/extensibility/debugger/stepping-in-break-mode)します。  
  
次に、デバッガーが中断モードとコードをステップ実行する必要があるときに発生するプロセスについて説明します。  
  
## <a name="stepping-process"></a>プロセスをステップ実行  
  
1.  呼び出す[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)で[STEPKIND](../../extensibility/debugger/reference/stepkind.md)と[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)ステップを実行する引数。  
  
2.  ステップが完了したら、送信、 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) stopping イベントとして。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

