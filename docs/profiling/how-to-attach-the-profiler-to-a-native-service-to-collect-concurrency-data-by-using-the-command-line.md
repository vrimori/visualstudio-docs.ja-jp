---
title: "方法: コマンド ラインを使用してプロファイラーをネイティブ サービスにアタッチし、同時実行データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: コマンド ラインを使用してプロファイラーをネイティブ サービスにアタッチし、同時実行データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、プロファイラーをネイティブ \(C\/C\+\+\) サービスにアタッチし、サンプリング メソッドによってプロセス データおよびスレッド同時実行データを収集する方法について説明します。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、Visual Studio インストール ディレクトリの \\Team Tools\\Performance Tools サブディレクトリにあります。  64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。  コマンド プロンプトでプロファイラーを使用するには、**コマンド プロンプト** ウィンドウの PATH 環境変数またはコマンド自体にツールのパスを追加します。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
  
 プロファイラーをサービスにアタッチしている間はデータ収集を一時停止し、完了後に再開できます。  プロファイル セッションを終了するには、サービスへのプロファイラーのアタッチを解除し、プロファイラーを明示的に終了する必要があります。  
  
## プロファイラーのアタッチ  
 プロファイラーをネイティブ サービスにアタッチするには、**VSPerfCmd** の **\/start** オプションおよび **\/attach** オプションを使用して、プロファイラーを初期化し、対象アプリケーションにアタッチします。  **\/start** と **\/attach**、およびそれぞれのオプションは、同じコマンド ライン上に指定できます。  **\/globaloff** オプションを追加して、対象アプリケーションの起動時にデータ収集を一時停止することもできます。  次に、**\/globalon** を使用してデータの収集を開始します。  
  
#### プロファイラーをネイティブ サービスにアタッチするには  
  
1.  サービスが実行されていない場合は、開始します。  
  
2.  コマンド プロンプトで次のコマンドを入力してプロファイラーを開始します。  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
    -   **\/start** を使用する場合は [\/output](../profiling/output.md)**:**`OutputFile` オプションを指定する必要があります。  `OutputFile` には、プロファイル データ \(.vsp\) ファイルの名前と場所を指定します。  
  
     **\/start**  オプションには次の表の任意のオプションを指定できます。  
  
    > [!NOTE]
    >  ほとんどのサービスで **\/user** および **\/crosssession** オプションが必要です。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|プロファイラーへのアクセスを許可するアカウントのオプションのドメインとユーザー名を指定します。|  
    |[\/crosssession](../profiling/crosssession.md)|他のログオン セッションにおけるプロセスのプロファイリングを有効にします。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter** と共にのみ使用します。  Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。  既定値は 500 です。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW \(Event Tracing for Windows\) イベントを指定します。  ETW イベントは独立した \(.etl\) ファイルに収集されます。|  
  
3.  コマンド プロンプトで次のコマンドを入力して、プロファイラーをサービスにアタッチします。  
  
     **VSPerfCmd \/attach:** `PID`  
  
     `PID` には、対象アプリケーションのプロセス ID またはプロセス名を指定します。  Windows タスク マネージャーで、実行中のすべてのプロセスのプロセス ID を参照できます。  
  
## データ収集の制御  
 対象アプリケーションの実行中は、VSPerfCmd.exe のオプションを使用してファイルへのデータ書き込みを開始および停止することにより、データ収集を制御できます。  データ収集を制御することにより、アプリケーションの起動や終了など、プログラム実行の特定部分のデータを収集できます。  
  
#### データ収集を開始および停止するには  
  
-   次の表に示すオプションの組み合わせにより、データ収集を開始および停止します。  個別のコマンド ラインで各オプションを指定します。  データ収集のオンとオフは複数回切り替えることができます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 \(**\/globalon**\) または停止 \(**\/globaloff**\) します。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|プロセス ID \(`PID`\) で指定されたプロセスのデータ収集を開始 \(**\/processon**\) または停止 \(**\/processoff**\) します。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** は、プロセス ID \(`PID`\) またはプロセス名 \(*ProcName*\) で指定したプロセスのデータ収集を開始します。  **\/detach** は、指定されたプロセスのデータ収集を停止します。プロセスが指定されていない場合は、すべてのプロセスのデータ収集を停止します。|  
  
## プロファイル セッションの終了  
 プロファイル セッションを終了するには、プロファイラーがデータ収集を停止している必要があります。  サービスを停止するか **VSPerfCmd \/detach** オプションを呼び出すことによって、同時実行メソッドを使用してプロファイリングが実行されているネイティブ サービスからのデータ収集を停止できます。  次に、**VSPerfCmd \/shutdown** オプションを呼び出して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。  
  
#### プロファイル セッションを終了するには  
  
1.  サービスを停止するか、コマンド プロンプトで次のコマンドを入力し、対象のアプリケーションからプロファイラーをデタッチします。  
  
     「**VSPerfCmd \/detach**」と入力します。  
  
2.  コマンド プロンプトに次のコマンドを入力し、プロファイラーを終了します。  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)