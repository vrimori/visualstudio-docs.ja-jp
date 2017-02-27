---
title: "プログラムへのアタッチ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、プログラムへのアタッチ"
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# プログラムへのアタッチ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

適切なポートでプログラムを登録したらデバッグ対象のプログラムにデバッガーをアタッチする必要があります。  
  
## 追加する方法を選択します  
 デバッグ セッションのマネージャーがデバッグ \(SDM\) 対象のプログラムにアタッチしようとする 3 とおりの方法があります。  
  
1.  [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) のメソッドによるデバッグ エンジンによって呼び出されるプログラムが \(たとえば解釈される言語の一般的な SDM\) はアタッチしたプログラムに関連付けられた [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) のオブジェクトから [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) のへのインターフェイスを取得します。  SDM が `IDebugProgramNodeAttach2` のインターフェイスを取得できる SDM は [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) のメソッドを呼び出します。  これはプログラムにアタッチされていないことおよびそのほかの例ではプログラムにアタッチしようとしたことを示す `IDebugProgramNodeAttach2::OnAttach` のメソッド `S_OK`。  
  
2.  SDM がアタッチされたプログラムからの [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) のインターフェイスを取得できる SDM は [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) のメソッドを呼び出します。  この方法はポートのサプライヤーしてリモートで起動プログラムで一般的です。  
  
3.  プログラムが `IDebugProgramNodeAttach2::OnAttach` または `IDebugProgramEx2::Attach` のメソッドによってアタッチできない場合 \(SDM\) まだ読み込まれていない場合の負荷が `CoCreateInstance` の関数を呼び出してデバッグ エンジンを [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドを呼び出します。  この方法はポートの仕入先にローカルで実行されるプログラムで一般的です。  
  
     カスタム ポートがサプライヤーのカスタム ポートの仕入先 `IDebugProgramEx2::Attach` のメソッドの実装の `IDebugEngine2::Attach` のメソッドを呼び出すこともできます。  通常この場合カスタム ポートの業者はリモート コンピューターでデバッグ エンジンを起動します。  
  
 添付ファイルにはデバッグ セッションの管理に [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) の \(SDM\) メソッドを呼び出すと行われます。  
  
 同じプロセスでアプリケーションをデバッグします [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) に次のメソッドを実行する必要がある場合に実行する場合 :  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 `IDebugEngine2::Attach` のメソッドが呼び出された後`IDebugEngine2::Attach` のメソッドの実装で次の手順を実行する :  
  
1.  SDM への [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) のイベント オブジェクトを送信します。  詳細については、「[イベントを送信します。](../../extensibility/debugger/sending-events.md)」を参照してください。  
  
2.  `IDebugEngine2::Attach` のメソッドに渡された [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) のオブジェクトの [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) のメソッドを呼び出します。  
  
     プログラムを識別するために使用されます。これは `GUID` を返します。  DE `GUID` はローカル プログラムを表すを返す必要があります `IDebugProgram2::GetProgramId` のオブジェクトでメソッドがインターフェイスで呼び出されると `IDebugProgram2` 保存されます。  
  
    > [!NOTE]
    >  `IDebugProgramNodeAttach2` のインターフェイスを実装する場合はプログラムの `GUID` は `IDebugProgramNodeAttach2::OnAttach` のメソッドに渡されます。  この `GUID` は `IDebugProgram2::GetProgramId` のメソッドによって返されるプログラムの `GUID` に使用されます。  
  
3.  DE にプログラムを表すために `IDebugProgram2` のローカル オブジェクト SDM が作成されたことを通知する [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) のイベント オブジェクトを送信します。  詳細については、「[イベントを送信します。](../../extensibility/debugger/sending-events.md)」を参照してください。  
  
    > [!NOTE]
    >  これは `IDebugEngine2::Attach` のメソッドに渡されたオブジェクトの `IDebugProgram2` 同じではありません。  `IDebugProgram2` の前に渡されたオブジェクトはポートによってのみ認識され別のオブジェクトです。  
  
## 参照  
 [添付ファイルの起動に基づく](../../extensibility/debugger/launch-based-attachment.md)   
 [イベントを送信します。](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)