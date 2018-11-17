---
title: 起動後のアタッチ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 416c05a7592d9f036a76a5d96537b4be917a0651
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774706"
---
# <a name="attaching-after-a-launch"></a>起動後のアタッチ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プログラムが起動された後に、デバッグ セッションはそのプログラムをデバッグ エンジン (DE) をアタッチする準備が。  
  
## <a name="design-decisions"></a>設計上の決定  
 通信は、共有のアドレス空間内で簡単であるため、デバッグ セッションと、DE、または、DE およびプログラムの間の通信を容易にする際になるかどうかを決める必要があります。 次の設定の選択します。  
  
-   方をデバッグ セッションと、DE 間の通信を容易にする、デバッグ セッションは、DE を共同作成し、プログラムにアタッチする DE を確認します。 これにより、デバッグ セッションと DE まとめて 1 つのアドレス空間、およびランタイム環境、およびプログラム間でまとめてできます。  
  
-   DE とプログラムの間のコミュニケーションを促進する方を提示した場合に、実行時環境は、DE、共同作成されます。 これにより、1 つのアドレス空間で SDM、DE、ランタイム環境、およびプログラム間でまとめてできます。 これは、スクリプト言語を実行する、インタープリターに実装されている DE の一般的な例です。  
  
    > [!NOTE]
    >  デがプログラムにアタッチする方法とは実装によって異なります。 デと、プログラム間の通信も実装に依存します。  
  
## <a name="implementation"></a>実装  
 プログラムでは、受信すると、セッション デバッグ マネージャー (SDM) まず、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)を起動するプログラムを表すオブジェクトを呼び出す、[アタッチ](../../extensibility/debugger/reference/idebugprogram2-attach.md)を引数としてメソッドを[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)以降であるオブジェクト、SDM にデバッグ イベントを渡すために使用します。 `IDebugProgram2::Attach`メソッドを呼び出して、 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッド。 SDM を受信する方法の詳細については、`IDebugProgram2`インターフェイスは、「[ポートへの通知](../../extensibility/debugger/notifying-the-port.md)します。  
  
 デバッグ中、通常、DE、インタープリターのスクリプトを実行の一部であるため、プログラムと同じアドレス空間で実行する必要がある、DE 場合、`IDebugProgramNodeAttach2::OnAttach`メソッドを返します。 `S_FALSE`、attach プロセスが完了したことを示します。  
  
 場合、デが、SDM のアドレス空間で実行する一方で、`IDebugProgramNodeAttach2::OnAttach`メソッドを返します`S_OK`または[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)インターフェイスがまったくで実装されていません、 [IDebugProgramNode2。](../../extensibility/debugger/reference/idebugprogramnode2.md)デバッグ中のプログラムに関連付けられているオブジェクト。 ここで、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドが最終的に、アタッチ操作を完了すると呼ばれます。  
  
 後者の場合、呼び出す必要がある、 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを`IDebugProgram2`に渡されたオブジェクト、`IDebugEngine2::Attach`メソッドは、ストア、`GUID`ローカル プログラムのオブジェクト、およびこれを返す`GUID`ときに、`IDebugProgram2::GetProgramId`メソッドがこのオブジェクトの後と呼ばれます。 `GUID`さまざまなデバッグ コンポーネント間で、プログラムを一意に識別するために使用します。  
  
 場合に注意してください、`IDebugProgramNodeAttach2::OnAttach`を返すメソッド`S_FALSE`、`GUID`メソッドに渡される、プログラムに使用しては、`IDebugProgramNodeAttach2::OnAttach`を設定するメソッド、`GUID`ローカル プログラムのオブジェクト。  
  
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

