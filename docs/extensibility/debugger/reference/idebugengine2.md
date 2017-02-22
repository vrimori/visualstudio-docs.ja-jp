---
title: "IDebugEngine2 | Microsoft Docs"
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
  - "IDebugEngine2"
helpviewer_keywords: 
  - "IDebugEngine2 インターフェイス"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ エンジンを表します \(DE\)。  例外の設定やオフにするとブレークポイントの作成からデバッグ セッションのさまざまな面を管理するために使用されます。  
  
## 構文  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはカスタム de\-DE によってプログラムのデバッグを管理するために実装されます。  このインターフェイスは機能しますが実装する必要があります。  
  
## 呼び出し元のメモ  
 このインターフェイスはデバッグ セッションのマネージャー \(SDM\) によってデバッグ セッションがマネージ例外が呼び出されブレークポイントを管理するために作成しde\-DE から送信された同期イベントに応答します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugEngine2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|DE によってデバッグ中のすべてのプログラムの列挙子を作成します。|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|DE をプログラムにアタッチします。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE の保留中のブレークポイントを作成します。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|DE が特定の例外を処理する方法を指定します。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|指定した例外を削除します。デバッグ エンジンによって処理されなくなります。|  
|[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md)|IDE の実行時に特定のアーキテクチャまたは言語に設定されている例外の一覧を削除します。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|DE の GUID を取得します。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|指定されたプログラムが不規則に終了したことおよびしますがプログラムへのすべての参照を削除しプログラムの破棄イベントを送信する必要があることを通知します。|  
|[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)|前に SDM に DE から送られた同期デバッグ イベントがされ処理されたことを示すにはSDM によって呼び出されます。|  
|[Setlocale 関数](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE のロケールを設定します。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|レジストリ ルートを DE で現在使用されて設定します。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|メトリックを設定します。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|この de\-DE によってデバッグ中のすべてのプログラムが実行を停止する要求は次にスレッドの 1 つが実行しようとします。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)