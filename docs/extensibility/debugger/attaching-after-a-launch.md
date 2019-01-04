---
title: 起動後のアタッチ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33bc38ca3e0c9b3bde07be48c74c31e4fc5148df
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922217"
---
# <a name="attach-after-a-launch"></a>起動の後のアタッチします。
プログラムを起動した後、デバッグ セッションとプログラムをデバッグ エンジン (DE) をアタッチする準備ができます。  
  
## <a name="design-decisions"></a>設計上の決定  
 2 つのデザイン方法を選択する必要があります通信が、共有のアドレス空間内で簡単にあるため、: デバッグ セッションと、DE 間の通信を設定します。 または、DE、およびプログラムの間の通信を設定します。 次の設定の選択します。  
  
-   デバッグ セッションと、DE 間の通信を設定する方を提示した場合に、デバッグ セッション、DE を共同作成し、のプログラムにアタッチする DE を尋ねます。 この設計のままに、デバッグ セッションと DE まとめて 1 つのアドレス空間、およびランタイム環境とプログラム別にまとめる。  
  
-   方、DE とプログラムの間の通信を設定する、実行時環境は共同、DE を作成します。 この設計は、別にまとめて 1 つのアドレス空間と、DE、実行時環境、およびプログラムに SDM を残します。 この設計は、スクリプト言語を実行する、インタープリターに実装されている DE の一般的な例です。  
  
    > [!NOTE]
    >  デがプログラムにアタッチする方法とは実装によって異なります。 デと、プログラム間の通信も実装に依存します。  
  
## <a name="implementation"></a>実装  
 プログラムでは、受信すると、セッション デバッグ マネージャー (SDM) まず、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)を起動するプログラムを表すオブジェクトを呼び出す、[アタッチ](../../extensibility/debugger/reference/idebugprogram2-attach.md)を引数としてメソッドを[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)以降であるオブジェクト、SDM にデバッグ イベントを渡すために使用します。 `IDebugProgram2::Attach`メソッドを呼び出して、 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッド。 SDM を受信する方法の詳細については、`IDebugProgram2`インターフェイスは、「[ポートへの通知](../../extensibility/debugger/notifying-the-port.md)します。  
  
 デバッグしている場合は、プログラムと同じアドレス空間で実行する必要があります、DE: DE は通常、スクリプトを実行しているインタープリターの一部であるため、`IDebugProgramNodeAttach2::OnAttach`メソッドを返します。`S_FALSE`します。 `S_FALSE`戻り値は、アタッチ プロセスが完了したことを示します。  
  
 かどうか、ただし、DE で実行、SDM のアドレス空間:`IDebugProgramNodeAttach2::OnAttach`メソッドを返します`S_OK`、または[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)ですべてのインターフェイスが実装されていません、 [IDebugProgramNode2。](../../extensibility/debugger/reference/idebugprogramnode2.md)をデバッグするプログラムに関連付けられているオブジェクト。 ここで、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドが最終的に、アタッチ操作を完了すると呼ばれます。  
  
 後者の場合、呼び出す必要がある、 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを`IDebugProgram2`に渡されたオブジェクト、`IDebugEngine2::Attach`メソッドは、ストア、`GUID`ローカル プログラムのオブジェクト、およびこれを返す`GUID`ときに、`IDebugProgram2::GetProgramId`メソッドがこのオブジェクトの後と呼ばれます。 `GUID`さまざまなデバッグ コンポーネント間で、プログラムを一意に識別するために使用します。  
  
 場合、`IDebugProgramNodeAttach2::OnAttach`を返すメソッド`S_FALSE`、`GUID`メソッドに渡される、プログラムに使用しては、`IDebugProgramNodeAttach2::OnAttach`を設定するメソッド、`GUID`ローカル プログラムのオブジェクト。  
  
 プログラムにし、スタートアップ イベントを送信する準備ができて、DE はアタッチされています。  
  
## <a name="see-also"></a>関連項目  
 [直接プログラムへのアタッチ](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [ポートへの通知](../../extensibility/debugger/notifying-the-port.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [アタッチ](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [添付](../../extensibility/debugger/reference/idebugengine2-attach.md)