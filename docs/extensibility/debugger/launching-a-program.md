---
title: "プログラムの起動 | Microsoft Docs"
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
  - "デバッグ エンジンを起動します。"
  - "起動するプログラム"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# プログラムの起動
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラムをデバッグするユーザーを IDE からデバッガーを実行するにはF5 キーを押すこともできます。  これは次のように接続している場合はプログラムにアタッチしてデバッグ エンジン \(DE\) に接続する IDE'S に最終的に実行される一連のイベントが :  
  
1.  IDE を初めて呼び出すソリューションのアクティブなプロジェクトのデバッグの設定を取得するプロジェクトのパッケージ。  設定はプログラムを作成するときに指定されたプログラムを実行するとが起動します。ディレクトリ環境変数ポート。  これらの設定はデバッグのパッケージに渡されます。  
  
2.  DE を指定するとde\-DE はプログラムを起動するオペレーティング システムを呼び出します。  プログラムを起動してプログラムの実行時環境が読み込まれます。  たとえばプログラムが MSIL で記述されておりプログラムを実行するために共通言語ランタイムが呼び出されます。  
  
     または  
  
     DE が指定されていない場合はポートはプログラムの実行時環境を読み込みますプログラムを起動するオペレーティング システムを呼び出します。  
  
    > [!NOTE]
    >  プログラムの起動に機能しますが使用される場合と同じ機能しますがプログラムにアタッチされている可能性があります。  
  
3.  によってプログラムが実行している DE またはポートがプログラムを起動しますかどうかまたはランタイム環境ではプログラムについてノードを作成しポートに通知します。  
  
    > [!NOTE]
    >  プログラムのノードをデバッグするプログラムの軽量な表現であるためにランタイム環境のプログラムのノードを作成することをお勧めします。  プログラムのノードを作成および登録するに全体の機能しますが読み込む必要はありません。  DE が IDE の過程で動作するように設計されているがIDE を実際に実行されていない場合はポートプログラムのノードを追加できるコンポーネントが必要です。  
  
 新しく作成されたプログラムは他のプログラムとともに同じ IDE から関係起動に関連していないか構成してデバッグ セッションがアタッチされます。  
  
 ユーザーが 1 番目の **F5** を押すとプログラムのデバッグ方法パッケージはソリューションのアクティブなプロジェクトのデバッグの設定を使用して <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> の構造を入力する <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> のメソッドによって開始 \(プログラムの種類に関連付けられた\) プロジェクトのパッケージ呼び出します。  この構造は <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> のメソッドを呼び出すことによってデバッグのパッケージに渡されます。  デバッグのパッケージはデバッグ対象プログラム \(SDM\) と関連付けられたデバッグ エンジンを呼び出してマネージャーのデバッグ セッションをインスタンス化します。  
  
 SDM に渡される引数の 1 つがプログラムの起動に使用される DE の GUID です。  
  
 DE GUID が `GUID_NULL` 場合SDM は de\-DE を共同作成しプログラムを起動する [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) のメソッドを呼び出します。  たとえばプログラムがネイティブ コードで記述されている場合`IDebugEngineLaunch2::LaunchSuspended``CreateProcess` と `ResumeThread` \(関数\) Win32 プログラムの実行に呼び出します。  
  
 プログラムを起動してプログラムの実行時環境が読み込まれます。  プログラムを実行するとします。ランタイム環境ではプログラムを記述する [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) のインターフェイスを作成し[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) にポートを通知するためにこのインターフェイスを渡します。  
  
 `GUID_NULL` が渡されるとポートのプログラムを起動します。  一度実行している場合はプログラム実行時環境でプログラムを記述する `IDebugProgramNode2` のインターフェイスを作成し`IDebugPortNotify2::AddProgramNode` に渡します。  これによりプログラムが実行しているポートを通知します。  SDM は実行中のプログラムをデバッグ エンジンをアタッチします。  
  
## このセクションの内容  
 [ポートへの通知](../../extensibility/debugger/notifying-the-port.md)  
 開始行われポートが通知されます。プログラムの後について説明します。  
  
 [起動した後にアタッチします。](../../extensibility/debugger/attaching-after-a-launch.md)  
 デバッグ セッションをプログラムで de\-DE をアタッチする準備が整ったときにドキュメント。  
  
## 関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動し式を評価などのさまざまなデバッグ タスクへのリンクが含まれます。