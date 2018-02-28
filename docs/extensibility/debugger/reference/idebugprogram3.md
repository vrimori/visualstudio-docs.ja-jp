---
title: "IDebugProgram3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cb827c875731134b9d8f9ea2833f3629ca0d3c36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram3"></a>IDebugProgram3
このインターフェイスを表しますが、プロセスで実行され、拡張するプログラム[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)スレッドに関する情報を提供することによりします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) とそのカスタム ポート業者は、プロセスでプログラムを表すためには、このインターフェイスを実装します。 セッションのデバッグ マネージャー (SDM) も情報を提供するには、このインターフェイスを実装[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベントが新しいプログラムのこのインターフェイスを返します。 このインターフェイスは、複数のインターフェイスの多くのメソッドのパラメーターとしても使用されます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgram3`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|プログラムを実行します。 実行するときに、ユーザーを表示するスレッドでデバッガーの情報を提供し、スレッドが返されます。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>コメント  
 プログラムは、プロセスで構成される 1 つまたは複数のプログラムの中に、特定のランタイムのアーキテクチャで実行されているスレッド コンテナーです。  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)