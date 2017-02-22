---
title: "プログラムに直接接続 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、プログラムへのアタッチ"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# プログラムに直接接続
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

通常既に実行中のプロセスのデバッグ対象にするユーザーはこのプロセスに従っています :  
  
1.  IDE では **ツール** \] メニューの  **デバッグの手順**  のコマンドを選択します。  
  
     **\[プロセス\]** ダイアログ ボックスが表示されます。  
  
2.  プロセスを選択し **アタッチ**  のをクリックします。  
  
     \[ENT0ENT\] ダイアログ ボックスが表示されコンピューターにインストール \(DEs\) されているすべてのデバッグ エンジンを示します。  
  
3.  選択されたプロセスをデバッグするために使用する DEs を指定しを ENT0ENT \[\] をクリックします。  
  
 デバッグのパッケージはデバッグ セッションを開始しDEs の一覧を渡します。  デバッグ セッションは選択されたプロセスに渡しこの一覧をコールバック関数とともに次に実行中のプログラムを列挙するプロセスを要求します。  
  
 プログラムによってユーザーの要求に応じてパッケージはデバッグ セッションのデバッグ マネージャーをインスタンス化し\(SDM\) 選択した DEs の一覧を渡します。  リストとともにデバッグのパッケージは [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) SDM にインターフェイスを渡します。  デバッグのパッケージは選択したプロセスに [IDebugProcess2:: アタッチ](../../extensibility/debugger/reference/idebugprocess2-attach.md) の呼び出しを DEs の一覧を渡します。  SDM はプロセスで実行するプログラムを列挙するためのポートの [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) を呼び出します。  
  
 これ以降各デバッグ エンジンは 2 種類の例外を除き [起動後のアタッチ](../../extensibility/debugger/attaching-after-a-launch.md) で説明したように一つのプログラムにアタッチされます。  
  
 効率についてはDEs はde\-DE に SDM とアドレス空間を共有するに実行される一連のプログラムがある場合はアタッチにグループ化します。  この場合[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) は [IDebugEngine2:: アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md) を呼び出しアタッチにはプログラムの配列をに渡します。  
  
 2 番目の例外は既に実行中のプログラムにアタッチする DE から送信されたスタートアップ イベントはエントリ ポイント イベントが含まれないようになります。  
  
## 参照  
 [起動した後、スタートアップ イベントを送信します。](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)