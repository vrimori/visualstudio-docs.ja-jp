---
title: "要求ポート業者インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973d191305383967aee1c7379fd203375a71c825
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="required-port-supplier-interfaces"></a>必要なポート業者インターフェイス
ポートのサプライヤーを実装する必要があります、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイス[。IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 ポートのサプライヤーは、ポートを提供、しているため、必要がありますもそれらを実装します。 そのため、次のインターフェイスを実装してする必要があります。  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     ポートをについて説明し、ポートで実行されているすべてのプロセスを列挙できます。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     起動して、ポート上のプロセスの終了を提供します。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     プログラムのノードの作成と破棄の通知にこのポートのコンテキスト内で実行されているプログラムのメカニズムを提供します。 詳細については、次を参照してください。[プログラム ノード](../../extensibility/debugger/program-nodes.md)です。  
  
-   `IConnectionPointContainer`  
  
     接続ポイントを提供[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)です。  
  
## <a name="port-supplier-operation"></a>ポートのサプライヤーの操作  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)シンクが処理されるときに通知を受信し、プログラムが作成され、ポートを破棄します。 ポートが送信するために必要な[IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)プロセスの作成時に、 [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)ポートでプロセスが破棄されるときです。 ポートが送信するために必要なも[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)プログラムが作成されたときと[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)ポートで実行中のプロセスで、プログラムが破棄されるとき。  
  
 ポート通常送信プログラムの作成し、破棄イベントへの応答、 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)と[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)メソッド、それぞれします。  
  
 ポートが起動し、両方の物理プロセスと論理のプログラムを終了するため、デバッグ エンジンによってもこのこれらのインターフェイスを実装する必要があります。  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     物理プロセスをについて説明します。 少なくとも次のメソッドを実装する必要があります。  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     SDM のアタッチし、自体をプロセスからデタッチするための手段を提供します。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     論理プログラムをについて説明します。 少なくとも次のメソッドを実装する必要があります。  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     このプログラムにアタッチする SDM のための手段を提供します。  
  
## <a name="see-also"></a>関連項目  
 [ポートのサプライヤーの実装](../../extensibility/debugger/implementing-a-port-supplier.md)