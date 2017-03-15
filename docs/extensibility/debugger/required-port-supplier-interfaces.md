---
title: "必要なポート サプライヤー インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ポートの供給業者、必要なインターフェイス"
  - "[デバッグ SDK] ポートのサプライヤーのデバッグ"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 必要なポート サプライヤー インターフェイス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ポートの業者は [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) のインターフェイスを実装する必要があります。       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 ポートのサプライヤーの提供ポートはそれらを実行する必要がある。  したがって次のインターフェイスを実装する必要があります :  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     ポートについて説明しポートで実行されているプロセスを列挙できます。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     ポートでプロセスを開始と終了を示します。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     プログラムのノードを作成および破棄をそれに通知するためにこのポートのコンテキスト内で動作するプログラムの機能を提供します。  詳細については、「[プログラムのノード](../../extensibility/debugger/program-nodes.md)」を参照してください。  
  
-   `IConnectionPointContainer`  
  
     [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) にコネクション ポイントを提供します。  
  
## ポートのサプライヤーの操作  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) シンクはプロセスとプログラムがポートに作成および破棄されたときに通知を受け取ります。  ポートはプロセスがポートで破棄されるとプロセスは [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) 作成時に [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) を送信する必要があります。  ポートはプログラムがポートで実行中のプロセスに破棄されるときにプログラムが [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 作成時に [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) を送信する必要があります。  
  
 ポートは [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) と [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) のメソッドに応じてプログラムの作成と破棄するイベントを個別に送信します。  
  
 ポートが物理的なプロセスと論理的なプログラムの両方を開始および終了するためこれらのインターフェイスはデバッグ エンジンが実装する必要があります :  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     物理的なプロセスについて説明します。  少なくとも次のメソッドを実装する必要があります :  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     からプロセスにアタッチ \/ デタッチ SDM に使用します。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     論理的なプログラムについて説明します。  少なくとも次のメソッドを実装する必要があります :  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     このプログラムにアタッチに SDM に使用します。  
  
## 参照  
 [ポートのサプライヤーを実装します。](../../extensibility/debugger/implementing-a-port-supplier.md)