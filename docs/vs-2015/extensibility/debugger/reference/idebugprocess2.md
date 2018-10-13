---
title: IDebugProcess2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5d1fcdb6df958a62ed23b3bc7e812e1f4a7e15f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218778"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、ポートで実行中のプロセスを表します。 ポートが、ローカル ポートの場合`IDebugProcess2`通常ローカル コンピューター上の物理的なプロセスを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、グループとしてプログラムを管理するカスタム ポートのサプライヤーによって実装されます。 ポート サプライヤーによってこのインターフェイスを実装する必要があります。  
  
 デバッグ エンジンは、によるプログラムの起動をサポートしている場合もこのインターフェイスを実装[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、このプロセスで識別されたプログラムのグループと対話するために主にセッション デバッグ マネージャー (SDM) によって呼び出されます。  
  
 呼び出す[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)または[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)このインターフェイスを取得します。 このインターフェイスは呼び出すことによっても返されます`IDebugEngineLaunch2::LaunchSuspended`します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcess2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|プロセスの説明を取得します。|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|このプロセスに含まれているプログラムを列挙します。|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|タイトル、フレンドリ名、またはプロセスのファイル名を取得します。|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|このプロセスが実行されているマシン server のインスタンスを取得します。|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|プロセスを終了します。|  
|[添付](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|プロセスにアタッチします。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|かどうか、SDM は、プロセスをデタッチできますを決定します。|  
|[デタッチ](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|デバッガーをプロセスからデタッチします。|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|システム プロセス識別子を取得します。|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|このプロセスには、グローバルに一意の識別子を取得します。|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [非推奨]|プロセスがデバッグ セッションの名前を取得します。<br /><br /> [非推奨とされます。 常に返す必要があります`E_NOTIMPL`]。|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|プロセスの実行中のスレッドを列挙します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|このプロセスの停止でコードを実行する次のプログラムを要求します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|このプロセスで実行されているポートを取得します。|  
  
## <a name="remarks"></a>Remarks  
 `IDebugProcess2` 1 つ以上含む[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

