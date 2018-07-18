---
title: 起動後にアタッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69f9f9cde76c5fa66294fd2cdbdc5252169e0183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104707"
---
# <a name="attaching-after-a-launch"></a>起動後にアタッチします。
プログラムが起動された後に、デバッグ セッションとプログラムをデバッグ エンジン (DE) をアタッチする準備ができてです。  
  
## <a name="design-decisions"></a>設計上の決定  
 通信は、共有のアドレス空間内で容易であるためかどうか方が有意義をデバッグ セッションと、DE、間、または、DE とプログラムの間の通信を容易にするかを決定する必要があります。 次の設定の選択します。  
  
-   方が有意義、デバッグ セッションと、DE 間の通信を容易にするために、デバッグ セッションは併置デを作成し、プログラムにアタッチする DE を要求します。 これにより、デバッグ セッションと DE 一緒に 1 つのアドレス空間、およびランタイム環境とプログラムの別のまとめられてなります。  
  
-   方が有意義デとプログラムの間の通信のために場合、実行時環境は、DE を共同作成します。 これにより、1 つのアドレス空間で SDM DE、ランタイム環境、およびプログラム間でまとめてなります。 これは、スクリプト言語を実行する、インタープリターに実装されている DE の一般的なです。  
  
    > [!NOTE]
    >  実装に依存するには、DE がプログラムにアタッチする方法です。 デとプログラムの間の通信も実装に依存します。  
  
## <a name="implementation"></a>実装  
 プログラムでは、受信すると、セッション デバッグ マネージャー (SDM) 最初、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)呼び出しを起動するプログラムを表すオブジェクトを[アタッチ](../../extensibility/debugger/reference/idebugprogram2-attach.md)渡して、メソッド、 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)以降では、オブジェクトが、SDM にデバッグ イベントを渡すために使用します。 `IDebugProgram2::Attach`メソッドを呼び出します、 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッドです。 SDM が受信する方法の詳細については、`IDebugProgram2`インターフェイスを参照してください[ポートへの通知](../../extensibility/debugger/notifying-the-port.md)です。  
  
 デバッグ中、通常、DE、スクリプトの実行、インタープリターの一部であるため、プログラムと同じアドレス空間で実行する必要がある、DE 場合、`IDebugProgramNodeAttach2::OnAttach`メソッドを返します。 `S_FALSE`、attach プロセスが完了したことを示すです。  
  
 、、DE、SDM のアドレス空間で実行している一方で、場合、`IDebugProgramNodeAttach2::OnAttach`メソッドを返します。`S_OK`または[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)インターフェイスがまったくに実装されていません、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)デバッグ中のプログラムに関連付けられているオブジェクト。 ここで、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドが最終的に、アタッチ操作を完了すると呼ばれます。  
  
 後者の場合、呼び出す必要があります、 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを`IDebugProgram2`に渡されたオブジェクト、`IDebugEngine2::Attach`メソッドは、ストア、`GUID`ローカル プログラムでオブジェクト、およびこれを返す`GUID`ときに、`IDebugProgram2::GetProgramId`メソッドがこのオブジェクトで、後でと呼ばれます。 `GUID`デバッグのさまざまなコンポーネント間で、プログラムを一意に識別するために使用します。  
  
 場合に注意してください、`IDebugProgramNodeAttach2::OnAttach`を返すメソッド`S_FALSE`、 `GUID` 、プログラムを使用するメソッドに渡され、は、`IDebugProgramNodeAttach2::OnAttach`を設定するメソッド、`GUID`ローカル プログラム オブジェクトにします。  
  
 プログラムにし、スタートアップ イベントを送信する準備ができて、DE はアタッチされています。  
  
## <a name="see-also"></a>関連項目  
 [プログラムに直接接続](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [ポートを通知します。](../../extensibility/debugger/notifying-the-port.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [アタッチ](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [添付](../../extensibility/debugger/reference/idebugengine2-attach.md)