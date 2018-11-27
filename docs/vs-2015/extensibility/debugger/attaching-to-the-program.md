---
title: プログラムへのアタッチ |Microsoft Docs
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
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c16c13b4dec412fa44be5cbfbbdd8494b805545
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777943"
---
# <a name="attaching-to-the-program"></a>プログラムへのアタッチ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

を、適切なポートとプログラムを登録した後は、デバッグするプログラムにデバッガーをアタッチする必要があります。  
  
## <a name="choosing-how-to-attach"></a>アタッチする方法を選択します。  
 セッション デバッグ マネージャー (SDM) がデバッグ中のプログラムにアタッチする試行が 3 つの方法はあります。  
  
1. 経由でデバッグ エンジンによって起動されたプログラム、 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 、SDM を取得します (たとえば、解釈された言語の標準)、メソッド、 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)からインターフェイス[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)にアタッチしたプログラムに関連付けられているオブジェクト。 SDM を取得できる場合、 `IDebugProgramNodeAttach2` 、インターフェイス、SDM を呼び出して、 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッド。 `IDebugProgramNodeAttach2::OnAttach`メソッドを返します。`S_OK`をプログラムにアタッチがないと、他の試行を行うプログラムにアタッチすることを示します。  
  
2. SDM を取得できる場合、 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) SDM コールにアタッチしたプログラムからインターフェイス、[アタッチ](../../extensibility/debugger/reference/idebugprogramex2-attach.md)メソッド。 この方法は、ポートのサプライヤーによってリモートで起動されたプログラムの一般的なものです。  
  
3. 場合は、プログラムをアタッチできません、`IDebugProgramNodeAttach2::OnAttach`または`IDebugProgramEx2::Attach`呼び出すことによって、メソッド、SDM の読み込み (読み込まれていない) 場合は、デバッグ エンジン、`CoCreateInstance`関数呼び出し、その後、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。 この方法は、ポートのサプライヤーによってローカルで起動されたプログラムの一般的なものです。  
  
    カスタム ポート サプライヤーを呼び出すことも、`IDebugEngine2::Attach`メソッドのカスタム ポート サプライヤーの実装では、`IDebugProgramEx2::Attach`メソッド。 通常この場合は、カスタム ポート サプライヤー エンジンを起動、デバッグ、リモート コンピューター上です。  
  
   セッション デバッグ マネージャー (SDM) を呼び出すと、添付ファイルは実現、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。  
  
   デバッグできるアプリケーションと同じプロセスで、DE を実行するかどうかは、次のメソッドを実装する必要があります[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)、  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  後に、`IDebugEngine2::Attach`メソッドが呼び出されるの実装で次の手順に従って、`IDebugEngine2::Attach`メソッド。  
  
1.  送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM にイベント オブジェクト。 詳細については、次を参照してください。[イベントの送信](../../extensibility/debugger/sending-events.md)します。  
  
2.  呼び出す、 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)に渡されたオブジェクト、`IDebugEngine2::Attach`メソッド。  
  
     これにより返されます、`GUID`プログラムを識別するために使用されます。 `GUID` DE を表すローカル プログラムを返す必要がある場合に、オブジェクトに格納する必要があります、`IDebugProgram2::GetProgramId`でメソッドが呼び出される、`IDebugProgram2`インターフェイス。  
  
    > [!NOTE]
    >  実装する場合、`IDebugProgramNodeAttach2`インターフェイス、プログラムの`GUID`に渡される、`IDebugProgramNodeAttach2::OnAttach`メソッド。 これは、`GUID`プログラムの使用は`GUID`によって返される、`IDebugProgram2::GetProgramId`メソッド。  
  
3.  送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 、SDM を通知するイベント オブジェクトをローカル`IDebugProgram2`DE にプログラムを表現するオブジェクトが作成されました。 詳細については、次を参照してください。[イベントの送信](../../extensibility/debugger/sending-events.md)します。  
  
    > [!NOTE]
    >  これは、同じ`IDebugProgram2`に渡されたオブジェクト、`IDebugEngine2::Attach`メソッド。 渡された以前`IDebugProgram2`オブジェクトは、ポートのみによって認識され、独立したオブジェクトします。  
  
## <a name="see-also"></a>関連項目  
 [起動ベースの添付ファイル](../../extensibility/debugger/launch-based-attachment.md)   
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

