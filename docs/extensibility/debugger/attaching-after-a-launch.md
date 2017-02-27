---
title: "起動した後にアタッチします。 | Microsoft Docs"
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
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 起動した後にアタッチします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラムが起動したらデバッグ セッションは前述のプログラムにデバッグ エンジンをアタッチ \(DE\) する準備が整いました。  
  
## デザインの決定  
 通信が共用アドレス空間内でより簡単であるためde\-DE とプログラムの間でデバッグ セッションで de\-DE 間の通信を簡単にとってわかりやすいまたは再作成するかを決める必要があります。  次の中から選択します :  
  
-   はデバッグ セッションと DE 間の通信を簡単に意味があるデバッグ セッションは de\-DE を共同作成しプログラムにアタッチすることを要求します。  これは1 種類のアドレス空間にデバッグ セッションと DE共通言語ランタイム環境を使用せずに別の内に設定します。  
  
-   これは de\-DE とプログラムの間の通信を簡単に意味があるランタイム環境では de\-DE を共同作成します。  これは1 種類のアドレス空間に SDMde\-DE のランタイム環境を受け入れ別の内に設定します。  これはスクリプト言語を実行するにはインタープリターによって実装される DE のが一般的です。  
  
    > [!NOTE]
    >  アプリケーションに機能しますが実装に依存がどのように指定します。  DE とプログラムの間の通信は実装に依存します。  
  
## 実装  
 デバッグ セッションのマネージャーが最初に起動する \(SDM\) プログラムを表す [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) のオブジェクトを受け取るとプログラムによってSDM に対してデバッグ イベントを渡すために後で使用する [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) のオブジェクトを渡す [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) のメソッドを呼び出します。  次に `IDebugProgram2::Attach` メソッドは [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) メソッドを呼び出します。  詳細についてはSDM が `IDebugProgram2` のインターフェイスを受け取った場合 [ポートへの通知](../../extensibility/debugger/notifying-the-port.md) を参照してください。  
  
 DE にスクリプトを実行しているインタープリターに含まれているためデバッグ対象のプログラムしますが同じアドレス空間に実装する必要がある場合はプロセスが完了したことを示す `IDebugProgramNodeAttach2::OnAttach` のメソッド `S_FALSE`。  
  
 一方SDM`IDebugProgramNodeAttach2::OnAttach` のメソッド `S_OK` または [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) のインターフェイスのアドレス空間にします runs がデバッグ対象プログラムと関連付けられている [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) のオブジェクトも実行されません。  この場合[Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドは最終的にアタッチ操作を完了するために呼び出されます。  
  
 後者の場合`IDebugProgram2::GetProgramId` のメソッドがこのオブジェクトで呼び出されると実行 `IDebugEngine2::Attach` のメソッドに渡されローカル オブジェクトに `GUID` プログラムを保存しこの `GUID` を返す `IDebugProgram2` のオブジェクトの [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) のメソッドを呼び出す必要があります。  `GUID` はさまざまなデバッグ コンポーネント間でプログラムを識別するために使用されます。  
  
 プログラムで使用する `S_FALSE` を返す `IDebugProgramNodeAttach2::OnAttach` のメソッドの場合は `GUID` がそのメソッドに渡されプログラムのローカル オブジェクトの `GUID` を設定する `IDebugProgramNodeAttach2::OnAttach` ではメソッドであることに注意してください。  
  
 DE はプログラムにアタッチされスタートアップ イベントを送信する準備ができました。  
  
## 参照  
 [プログラムに直接接続](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [ポートへの通知](../../extensibility/debugger/notifying-the-port.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)