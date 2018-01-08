---
title: "プログラムを終了して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4d1cb3176585dce135b19f125af55db799fed4b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="terminating-a-program"></a>プログラムの終了
1 つのスレッドで 1 つのプログラムの終了の説明を次に示します。  
  
## <a name="termination-process"></a>終了プロセス  
  
1.  DE 送信、 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 、有効な[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)です。  
  
2.  DE 送信、 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 、有効な[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)です。  
  
 IDE は、デザイン モードに入ります。 デバッグ エンジンまたはランタイム環境呼び出し[IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)ポートからプログラムを削除します。  
  
## <a name="see-also"></a>参照  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)