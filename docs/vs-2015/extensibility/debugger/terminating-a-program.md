---
title: プログラムの終了 |Microsoft Docs
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
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e15fa5746b5cd7fae66574ec0d318cad1184cfdd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861203"
---
# <a name="terminating-a-program"></a>プログラムの終了
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

1 つのスレッドで 1 つのプログラムの終了の説明を次に示します。  
  
## <a name="termination-process"></a>終了プロセス  
  
1. DE 送信、 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)有効な[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)します。  
  
2. DE 送信、 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)有効な[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)します。  
  
   IDE は、デザイン モードに入ります。 デバッグ エンジンまたはランタイム環境は[IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)ポートからプログラムを削除します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

