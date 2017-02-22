---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "IDebugProcess2 インターフェイス"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはポートで実行中のプロセスを表します。  ポートがローカルの場合`IDebugProcess2` はローカル コンピューターの物理的なプロセスを表します。  
  
## 構文  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはカスタム ポートの仕入先によってグループとしてプログラムを管理するために実装されます。  このインターフェイスはポートの仕入先に実装する必要があります。  
  
 デバッグ エンジンは[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) してプログラムを起動サポートする場合このインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスはデバッグ セッションのマネージャー \(SDM\) によってこのプロセスで識別されるプログラムのグループと対話するため主に呼び出されます。  
  
 このインターフェイスを取得するに [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) または [GetProcess](../Topic/IDebugPort2::GetProcess.md) を呼び出します。  このインターフェイスは`IDebugEngineLaunch2::LaunchSuspended` を呼び出すことによって返されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProcess2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|プロセスの詳細を取得します。|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|このプロセスに含まれるプログラムを列挙します。|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|プロセスのタイトル表示名またはファイル名を取得します。|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|このプロセスが実行されているコンピューターにサーバーのインスタンスを取得します。|  
|[終了](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|プロセスを終了します。|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|プロセスにアタッチされます。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM がプロセスをデタッチできるかどうかを判断します。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|プロセスからデバッガーをデタッチします。|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|システムのプロセス識別子を取得します。|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|このプロセスのグローバル一意識別子を取得します。|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[deprecated\]|プロセスをデバッグ セッションの名前を取得します。<br /><br /> \[deprecated。  `E_NOTIMPL` を常に返す必要です。\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|プロセスで実行中のスレッドを列挙します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|停止要求このプロセスの次のプログラム コードを実行する。|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|このプロセスが実行されているポートを取得します。|  
  
## 解説  
 `IDebugProcess2` は [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) の一つ以上のインターフェイスが含まれています。  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../Topic/IDebugPort2::GetProcess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [次へ](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)