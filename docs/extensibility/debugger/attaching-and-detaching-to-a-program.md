---
title: "アタッチとデタッチ プログラム | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、プログラムへのアタッチ"
  - "デバッグ エンジンは、プログラムからのデタッチ"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# アタッチとデタッチ プログラム
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーをアタッチすると適切な属性をメソッドとイベントの正しいシーケンスを送信する必要があります。  
  
## メソッドおよびイベントのシーケンス  
  
1.  デバッグ セッションのマネージャーは \(SDM\) [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) のメソッドを呼び出します。  
  
     次の方法の \(DE\) `IDebugProgramNodeAttach2::OnAttach` のメソッドは1 次に何が起こるかをデバッグ エンジンのプロセス モデルに基づいて。  
  
     `S_FALSE` が返された場合デバッグ エンジンはプログラムに正常にアタッチされています。  アタッチするプロセスを完了するには[Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドが呼び出されます。  
  
     `S_OK` が返された場合はde\-DE SDM と同じプロセスに読み込む必要があります。  SDM は次のタスクを実行します :  
  
    1.  DE エンジンの情報を取得する呼び出し [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)。  
  
    2.  DE を共同作成します。  
  
    3.  [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) を呼び出します。  
  
2.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)。  
  
3.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)。  
  
4.  DE sends `EVENT_SYNC_STOP` の属性の SDM への [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)。  
  
 プログラムからデタッチ次のように単純な行の手順で :  
  
1.  SDM は [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md) を呼び出します。  
  
2.  DE sends [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)