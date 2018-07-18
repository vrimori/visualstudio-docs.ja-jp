---
title: プログラムへのアタッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c9719f6258f3bbb5cc8323693001c7f1a9d47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107869"
---
# <a name="attaching-to-the-program"></a>プログラムへのアタッチ
適切なポートに、プログラムを登録した後をデバッグするプログラムにデバッガーをアタッチする必要があります。  
  
## <a name="choosing-how-to-attach"></a>アタッチする方法を選択します。  
 セッション デバッグ マネージャー (SDM) がデバッグ中のプログラムにアタッチしよう 3 つの方法があります。  
  
1.  経由でデバッグ エンジンによって起動されたプログラムを[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (たとえば、解釈された言語の標準)、メソッド、SDM の取得、 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)からインターフェイス[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)にアタッチされているプログラムに関連付けられているオブジェクト。 SDM を取得できる場合、 `IDebugProgramNodeAttach2` 、インターフェイス、SDM を呼び出して、 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッドです。 `IDebugProgramNodeAttach2::OnAttach`メソッドを返します。`S_OK`プログラムにアタッチしてできませんされ、他の試行をプログラムにアタッチするできることを示します。  
  
2.  SDM を取得できる場合、 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) SDM の呼び出しにアタッチされているプログラムからインターフェイス、[アタッチ](../../extensibility/debugger/reference/idebugprogramex2-attach.md)メソッドです。 このアプローチは通常ポート業者によってリモートで起動されたプログラムです。  
  
3.  を通じてプログラムをアタッチすることはできない場合、`IDebugProgramNodeAttach2::OnAttach`または`IDebugProgramEx2::Attach`を呼び出して、メソッド、SDM を読み込みます (読み込まれていない) 場合は、デバッグ エンジン、`CoCreateInstance`関数を呼び出し、続いて、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドです。 このアプローチは通常ポート業者によってローカルで起動されたプログラムです。  
  
     呼び出すカスタム ポート業者のことも、`IDebugEngine2::Attach`メソッドのカスタム ポート業者の実装では、`IDebugProgramEx2::Attach`メソッドです。 通常このケースでは、カスタム ポート サプライヤー エンジンを起動、デバッグ、リモート コンピューター上です。  
  
 セッションのデバッグ マネージャー (SDM) を呼び出すときに添付ファイルが実現される、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドです。  
  
 デバッグするには、アプリケーションと同じプロセスで、DE を実行するかどうかは、次のメソッドを実装する必要があります[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)、  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 後に、`IDebugEngine2::Attach`メソッドが呼び出されると、以下の手順の実装で、`IDebugEngine2::Attach`メソッド。  
  
1.  送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM にイベント オブジェクトです。 詳細については、次を参照してください。[送信イベント](../../extensibility/debugger/sending-events.md)です。  
  
2.  呼び出す、 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)に渡されたオブジェクト、`IDebugEngine2::Attach`メソッドです。  
  
     これを返します、`GUID`プログラムを識別するために使用されます。 `GUID`に返す必要がある場合に、DE、ローカル プログラムで表しますオブジェクトに格納する必要があります、`IDebugProgram2::GetProgramId`メソッドが、`IDebugProgram2`インターフェイスです。  
  
    > [!NOTE]
    >  実装する場合、`IDebugProgramNodeAttach2`インターフェイス、プログラムの`GUID`に渡される、`IDebugProgramNodeAttach2::OnAttach`メソッドです。 これは、`GUID`はプログラムのため`GUID`によって返される、`IDebugProgram2::GetProgramId`メソッドです。  
  
3.  送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 、SDM に通知するイベント オブジェクトをローカル`IDebugProgram2`デにプログラムを表すオブジェクトが作成されました。 詳細については、「[送信イベント](../../extensibility/debugger/sending-events.md)です。  
  
    > [!NOTE]
    >  これは、同じ`IDebugProgram2`に渡されたオブジェクト、`IDebugEngine2::Attach`メソッドです。 渡された以前`IDebugProgram2`オブジェクトは、ポートのみによって認識され、別のオブジェクトは、します。  
  
## <a name="see-also"></a>関連項目  
 [添付ファイルの起動に基づく](../../extensibility/debugger/launch-based-attachment.md)   
 [イベントの送信](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [アタッチ](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [添付](../../extensibility/debugger/reference/idebugengine2-attach.md)