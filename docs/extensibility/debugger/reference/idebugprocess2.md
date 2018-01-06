---
title: "IDebugProcess2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2
helpviewer_keywords: IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 896448526f41514fb74b385f8605839908708305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2"></a>IDebugProcess2
このインターフェイスは、ポートで実行中のプロセスを表します。 ポートの場合、ローカル ポートし`IDebugProcess2`通常、ローカル コンピューター上の物理プロセスを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、グループとしてプログラムを管理するカスタム ポート業者によって実装されます。 ポート業者によっては、このインターフェイスを実装する必要があります。  
  
 デバッグ エンジンは、によるプログラムの起動をサポートしている場合もこのインターフェイスを実装[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、このプロセスで識別されたプログラムのグループと対話するために、主にセッション デバッグ マネージャー (SDM) によって呼び出されます。  
  
 呼び出す[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)または[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)このインターフェイスを取得します。 このインターフェイスは呼び出すことによっても返されます`IDebugEngineLaunch2::LaunchSuspended`です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcess2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|プロセスの説明を取得します。|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|このプロセスに含まれているプログラムを列挙します。|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|タイトル、フレンドリ名、または、プロセスのファイル名を取得します。|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|このプロセスが実行されるマシン server のインスタンスを取得します。|  
|[終了](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|プロセスを終了します。|  
|[添付](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|プロセスにアタッチします。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM がプロセスを切り離すことができるかどうかを判断します。|  
|[デタッチ](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|プロセスからデバッガーをデタッチします。|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|システム プロセス識別子を取得します。|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|このプロセスには、グローバルに一意の識別子を取得します。|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATED]|プロセスのデバッグは、セッションの名前を取得します。<br /><br /> [非推奨です。 常に返す必要があります`E_NOTIMPL`]。|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|プロセスで実行中のスレッドを列挙します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|このプロセスの停止にコードを実行している次のプログラムを要求します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|このプロセスで実行されているポートを取得します。|  
  
## <a name="remarks"></a>コメント  
 `IDebugProcess2` 1 つ以上含む[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)