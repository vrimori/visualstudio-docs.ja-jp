---
title: "方法: コマンド ラインを使用してプロファイラーを ASP.NET Web アプリケーションにアタッチし、同時実行データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: コマンド ラインを使用してプロファイラーを ASP.NET Web アプリケーションにアタッチし、同時実行データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、プロファイラーを ASP.NET アプリケーションにアタッチし、プロセス データおよびスレッド同時実行データを収集する方法について説明します。  
  
 プロファイリング ツールのコマンド ライン ツールは、Visual Studio インストール ディレクトリの \\Team Tools\\Performance Tools サブディレクトリにあります。  64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。  コマンド プロンプトでプロファイラーを使用するには、**コマンド プロンプト** ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
  
 同時実行データを収集するには、Web サイトをホストする ASP.NET ワーカー プロセスにプロファイラーをアタッチします。  プロファイラーをアプリケーションにアタッチしている間はデータ収集を一時停止し、完了後に再開できます。  プロファイル セッションを終了するには、アプリケーションへのプロファイラーのアタッチを解除し、プロファイラーを明示的に終了する必要があります。  ほとんどの場合、セッションの最後にプロファイル環境変数を消去する必要があります。  
  
## プロファイラーのアタッチ  
  
#### プロファイラーを ASP.NET アプリケーションにアタッチするには  
  
1.  次のコマンドを入力してプロファイラーを起動します。  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency \/output:**`OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) オプションは、プロファイラーを初期化して、リソース競合データを収集します。  
  
    -   **\/start** を使用する場合は [\/output](../profiling/output.md)**:**`OutputFile` オプションを指定する必要があります。  `OutputFile` には、プロファイル データ \(.vsp\) ファイルの名前と場所を指定します。  
  
     **\/start**  オプションには次の表の任意のオプションを指定できます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|プロファイラーへのアクセスを許可するアカウントのオプションのドメインとユーザー名を指定します。|  
    |[\/crosssession](../profiling/crosssession.md)|他のログオン セッションにおけるプロセスのプロファイリングを有効にします。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter** と共にのみ使用します。  Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。  既定値は 500 です。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW \(Event Tracing for Windows\) イベントを指定します。  ETW イベントは独立した \(.etl\) ファイルに収集されます。|  
  
2.  一般的な方法で ASP.NET アプリケーションを起動します。  
  
3.  コマンド **VSPerfCmd \/attach:**`PID` \[**\/targetclr:**`Version`\] を入力して、プロファイラーを ASP.NET ワーカー プロセスにアタッチします。  
  
    -   `PID` には、ASP.NET ワーカー プロセスの ID または名前を指定します。  Windows タスク マネージャーで、実行中のすべてのプロセスのプロセス ID を参照できます。  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` には、アプリケーションに複数のバージョンのランタイムが読み込まれている場合に、プロファイリングを行う共通言語ランタイム \(CLR: Common Language Runtime\) のバージョンを指定します。  このパラメーターは省略できます。  
  
## データ収集の制御  
 アプリケーションの実行中は、VSPerfCmd.exe のオプションを使用してファイルへのデータ書き込みを開始または停止することにより、データ収集を制御できます。  データ収集を制御することにより、アプリケーションの起動や終了など、プログラム実行の特定部分のデータを収集できます。  
  
#### データ収集を開始および停止するには  
  
-   次の表に示す VSPerfCmd オプションの組み合わせにより、データ収集を開始および停止します。  個別のコマンド ラインで各オプションを指定します。  データ収集のオンとオフは複数回切り替えることができます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 \(**\/globalon**\) または停止 \(**\/globaloff**\) します。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|プロセス ID \(`PID`\) で指定されたプロセスのデータ収集を開始 \(**\/processon**\) または停止 \(**\/processoff**\) します。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** は、プロセス ID \(`PID`\) またはプロセス名 \(*ProcName*\) で指定したプロセスのデータ収集を開始します。  **\/detach** は、指定されたプロセスのデータ収集を停止します。プロセスが指定されていない場合は、すべてのプロセスのデータ収集を停止します。|  
  
## プロファイル セッションの終了  
 プロファイル セッションを終了するには、プロファイラーがデータ収集を停止している必要があります。  データ収集は、ASP.NET ワーカー プロセスを再起動するか **VSPerfCmd \/detach** オプションを呼び出し、同時実行メソッドを使用してプロファイリングを実行したアプリケーションから停止できます。  次に、**VSPerfCmd \/shutdown** オプションを呼び出して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。  **VSPerfClrEnv \/globaloff** コマンドによってプロファイル環境変数は消去されますが、コンピューターを再起動するまでシステム構成はリセットされません。  
  
#### プロファイル セッションを終了するには  
  
1.  対象のアプリケーションを終了するか、コマンド プロンプトで次のコマンドを入力し、アプリケーションからプロファイラーをデタッチします。  
  
     **VSPerfCmd \/detach**  
  
2.  コマンド プロンプトに次のコマンドを入力し、プロファイラーを終了します。  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 参照  
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)