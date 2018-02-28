---
title: "IDebugEngine2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 95a1a8c48bd6eab0f21ccc85a125b5d10f42ef4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2"></a>IDebugEngine2
このインターフェイスは、デバッグ エンジン (DE) を表します。 設定され、例外をクリアするブレークポイントの作成から、デバッグ セッションでのさまざまな側面を管理に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、プログラムのデバッグを管理するカスタム DE によって実装されます。 デによってこのインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、セッションのデバッグ マネージャー例外を管理する、ブレークポイントを作成、デによって送信された同期イベントに応答してなど、デバッグ セッションを管理するには、(SDM) によって呼び出されます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEngine2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|列挙子、DE では、デバッグされているすべてのプログラムを作成します。|  
|[添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)|プログラムに、DE をアタッチします。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|デに保留中のブレークポイントを作成します。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|デが特定の例外を処理する方法を指定します。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|不要になったデバッグ エンジンによって処理されるように、指定された例外を削除します。|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|IDE が特定のランタイム アーキテクチャまたは言語の設定で例外の一覧を削除します。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|デの GUID を取得します。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|指定されたプログラムが正しく終了になっていると、DE がプログラムへのすべての参照をクリーンアップしてプログラムを送信する必要がある、DE 破棄イベントを通知します。|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|以前に送信した、DE によって、SDM を同期のデバッグ イベントが受信され、処理を示すために SDM によって呼び出されます。|  
|[Setlocale、_wsetlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|デのロケールを設定します。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|現在、DE が使用してレジストリ ルートを設定します。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|メトリックを設定します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|この DE によってデバッグされているすべてのプログラムが次回の試行を実行するとき、スレッドの 1 つの実行を停止することを要求します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)