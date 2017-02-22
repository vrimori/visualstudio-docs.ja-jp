---
title: "デバッガーを起動します。 | Microsoft Docs"
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
  - "[デバッグの SDK] のデバッグ、デバッガーを起動します。"
  - "起動するデバッガー [Debugging SDK]"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# デバッガーを起動します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーを起動適切な属性をメソッドとイベントの正しいシーケンスを送信する必要があります。  
  
## メソッドおよびイベントのシーケンス  
  
1.  セッション マネージャーは \(SDM\) ENT2ENT \[デバッグ\] メニューのをクリックし **開始**  を選択することによって呼び出されます。  詳細については、「[プログラムの起動](../../extensibility/debugger/launching-a-program.md)」を参照してください。  
  
2.  SDM は [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) のメソッドを呼び出します。  
  
3.  次の方法の \(DE\) `IDebugProgramNodeAttach2::OnAttach` のメソッドは1 次に何が起こるかをデバッグ エンジンのプロセス モデルに基づいて。  
  
     `S_FALSE` が返された場合デバッグ エンジンは仮想マシン \(DE\) のプロセスに読み込まれている必要があります。  
  
     または  
  
     `S_OK` が返された場合はde\-DE SDM プロセスに読み込まれている必要があります。  SDM は次のタスクを実行します :  
  
    1.  DE エンジンの情報を取得する呼び出し [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)。  
  
    2.  DE を共同作成します。  
  
    3.  [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) を呼び出します。  
  
4.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)。  
  
5.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)。  
  
6.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)。  
  
7.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)。  
  
8.  DE sends `EVENT_SYNC` の属性の SDM への [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)   
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)