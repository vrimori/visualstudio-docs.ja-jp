---
title: ポート サプライヤー インターフェイスに必要な |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 960cd5668fe49ba50e79f036848948ec8e0bbfc2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536984"
---
# <a name="required-port-supplier-interfaces"></a>必須のポート サプライヤー インターフェイス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ポート サプライヤー インターフェイスのために必要な](https://docs.microsoft.com/visualstudio/extensibility/debugger/required-port-supplier-interfaces)します。  
  
ポート サプライヤーを実装する必要があります、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイス[。IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 ポート サプライヤーのポートを提供するためする必要がありますも実装します。 そのため、次のインターフェイスを実装にする必要があります。  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     ポートについて説明し、ポートで実行されているすべてのプロセスを列挙できます。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     起動して、ポート上のプロセスを終了しています。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     プログラム ノードの作成と破棄のことを通知にこのポートのコンテキスト内で実行されるプログラム メカニズムを提供します。 詳細については、次を参照してください。[プログラム ノード](../../extensibility/debugger/program-nodes.md)します。  
  
-   `IConnectionPointContainer`  
  
     接続ポイントを提供します[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)します。  
  
## <a name="port-supplier-operation"></a>ポート サプライヤーの操作  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)シンクの場合、プロセスの通知を受信し、プログラムが作成され、ポートを破棄します。 ポートが送信に必要な[IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)プロセスが作成されたときと[IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)ポートでプロセスを破棄する場合。 ポートが送信する必要も[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)プログラムが作成されたときと[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)ポートで実行中のプロセスでプログラムを破棄する場合。  
  
 ポート通常送信プログラムの作成し、破棄イベントへの応答、 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)と[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)メソッドでは、それぞれします。  
  
 ポートを起動し、両方の物理プロセスと論理プログラムの終了、ために、デバッグ エンジンでもこのこれらのインターフェイスを実装する必要があります。  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     物理的なプロセスをについて説明します。 少なくとも、次のメソッドを実装する必要があります。  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     アタッチし、自身のプロセスからデタッチ SDM の方法を提供します。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     論理プログラムをについて説明します。 少なくとも、次のメソッドを実装する必要があります。  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     このプログラムにアタッチする SDM の方法を提供します。  
  
## <a name="see-also"></a>関連項目  
 [ポートのサプライヤーの実装](../../extensibility/debugger/implementing-a-port-supplier.md)

