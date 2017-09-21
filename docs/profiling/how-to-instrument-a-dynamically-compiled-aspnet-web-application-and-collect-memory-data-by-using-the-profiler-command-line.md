---
title: "方法: プロファイラーのコマンド ラインを使用して動的にコンパイルされた ASP.NET Web アプリケーションをインストルメントし、メモリ データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: プロファイラーのコマンド ラインを使用して動的にコンパイルされた ASP.NET Web アプリケーションをインストルメントし、メモリ データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、動的にコンパイルされた [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションの .NET のメモリ割り当てやオブジェクトの有効期間に関する詳細データをインストルメンテーションによるプロファイリング方式によって収集する方法を説明します。  
  
> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] インストール ディレクトリの \\Team Tools\\Performance Tools サブディレクトリにあります。  64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。  プロファイラーのコマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションからパフォーマンス データを収集するには、対象アプリケーションの web.config ファイルを変更して、[VSInstr.exe](../profiling/vsinstr.md) というツールを有効にすることで、動的にコンパイルされたアプリケーション ファイルをインストルメントできるようにします。  その上で、[VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) ツールを使用して、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションをホストするサーバーを構成し、適切な環境変数を設定して .NET のメモリ プロファイリングを有効にし、コンピューターを再起動します。  
  
 データを収集するには、プロファイラーを起動してから対象アプリケーションを実行します。  プロファイラーがアプリケーションに適用されている間は、データ収集の一時停止や再開ができます。必要なデータを収集できたら、アプリケーションを終了し、インターネット インフォメーション サービス \(IIS: Internet Information Services\) ワーカー プロセスを終了してから、プロファイラーを終了します。  
  
 プロファイリング作業が完了したら、Web.config ファイルと Web サーバーを元の状態に戻します。  
  
## ASP.NET Web アプリケーションおよび Web サーバーの構成  
  
#### ASP.NET Web アプリケーションおよび Web サーバーを構成するには  
  
1.  対象アプリケーションの web.config ファイルを変更します。  「[方法: Web.config ファイルを変更して、動的にコンパイルされた ASP.NET Web アプリケーションをインストルメント化およびプロファイルする](../Topic/How%20to:%20Modify%20Web.Config%20Files%20to%20Instrument%20and%20Profile%20Dynamically%20Compiled%20ASP.NET%20Web%20Applications.md)」を参照してください。  
  
2.  Web アプリケーションをホストするコンピューターで、コマンド プロンプト ウィンドウを開きます。  
  
3.  プロファイル環境変数を初期化します。  Type:  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     または  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** を使用すると、メモリの割り当てデータを収集できます。  
  
    -   **\/globaltracegclife** を使用すると、メモリの割り当てデータとオブジェクトの有効期間データを収集できます。  
  
4.  コンピューターを再起動します。  
  
## プロファイル セッションの実行  
  
#### ASP.NET Web アプリケーションのプロファイリングを行うには  
  
1.  プロファイラーを起動します。  Type:  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   **\/start:trace** オプションによってプロファイラーが初期化されます。  
  
    -   **\/start** を使用する場合は **\/output:**`OutputFile` オプションを指定する必要があります。  `OutputFile` には、プロファイル データ \(.vsp\) ファイルの名前と場所を指定します。  
  
     **\/start:trace** オプションを使用する場合は、次のうちいずれかのオプションを指定できます。  
  
    > [!NOTE]
    >  **\/user** オプションと **\/crosssession** オプションは、通常、ASP.NET アプリケーションで必要です。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを所有するアカウントのドメインおよびユーザー名を指定します \(省略可能\)。  このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合に指定する必要があります。  この名前は、Windows タスク マネージャーの \[プロセス\] タブの \[ユーザー名\] 列に表示されます。|  
    |[\/crosssession](../profiling/crosssession.md)|他のセッションにおけるプロセスのプロファイリングを有効にします。  このオプションは、アプリケーションが別のセッションで実行されている場合に必要です。  セッション ID は、Windows タスク マネージャーの \[プロセス\] タブの \[セッション ID\] 列に表示されます。  **\/crosssession** の省略形として、**\/CS** を指定することができます。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|データ収集を一時停止した状態でプロファイラーを起動します。  プロファイリングを再開するには、[\/globalon](../profiling/globalon-and-globaloff.md) を使用します。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|`Config` で指定されたプロセッサのパフォーマンス カウンターから情報を収集します。  カウンター情報は、プロファイル イベントが発生するたびに、収集されたデータに追加されます。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter** と共にのみ使用します。  Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。  既定値は 500 ミリ秒です。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW \(Event Tracing for Windows\) イベントを指定します。  ETW イベントは独立した \(.etl\) ファイルに収集されます。|  
  
2.  一般的な方法で [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションを起動します。  
  
## データ収集の制御  
 対象アプリケーションの実行中は、**VSPerfCmd.exe** のオプションを使用して、プロファイラーのデータ ファイルへのデータ書き込みを開始および停止することにより、データ収集を制御できます。  データ収集を制御することにより、アプリケーションの起動や終了など、プログラム実行の特定の部分についてのデータ収集を行うことができます。  
  
#### データ収集を開始および停止するには  
  
-   次に示すオプションの組み合わせにより、データ収集を開始および停止します。  個別のコマンド ラインで各オプションを指定します。  データ収集のオンとオフは複数回切り替えることができます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 \(**\/globalon**\) または停止 \(**\/globaloff**\) します。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|プロセス ID \(`PID`\) で指定されたプロセスのデータ収集を開始 \(**\/processon**\) または停止 \(**\/processoff**\) します。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|スレッド ID \(`TID`\) で指定されたスレッドのデータ収集を開始 \(**\/threadon**\) または停止 \(**\/threadoff**\) します。|  
  
-   **VSPerfCmd.exe** [\/mark](../profiling/mark.md) オプションを使用して、データ ファイルにプロファイル マークを挿入することもできます。  **\/mark** コマンドは、ID、タイムスタンプ、およびオプションでユーザー定義の文字列を追加します。  マークは、プロファイラー レポートおよびデータ ビューでデータをフィルター処理するために使用できます。  
  
## プロファイル セッションの終了  
 プロファイル セッションを終了するには、対象の [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションを終了し、IIS を終了してプロファイリング対象プロセスを終了してから、プロファイラーを終了します。  その後、IIS を再起動します。  
  
#### プロファイル セッションを終了するには  
  
1.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションを終了します。  
  
2.  IIS をリセットして、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを終了します。  Type:  
  
     **IISReset \/stop**  
  
3.  プロファイラーをシャットダウンします。  Type:  
  
     **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
4.  IIS を再起動します。  Type:  
  
     **IISReset \/start**  
  
## アプリケーションおよびコンピューターの構成の復元  
 すべてのプロファイリングを完了したら、まず web.config ファイルを置き換え、プロファイル環境変数を削除します。次に、コンピューターを再起動して、サーバーと [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションを元の状態に戻します。  
  
#### アプリケーションとコンピューターの構成を元に戻すには  
  
1.  web.config ファイルを元のファイルに置き換えます。  
  
2.  \(省略可能\)   プロファイル環境変数を削除します。  Type:  
  
     **VSPerfCmd \/globaloff**  
  
3.  コンピューターを再起動します。  
  
## 参照  
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md)