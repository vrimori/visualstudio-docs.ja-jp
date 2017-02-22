---
title: "サンプリングを使用したパフォーマンス統計情報の収集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイリング ツール、サンプリング"
  - "サンプリング プロファイル方法"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# サンプリングを使用したパフォーマンス統計情報の収集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] プロファイリング ツールでサンプリング メソッドを使用すると、10,000,000 プロセッサ サイクル \(1 GH のコンピューターでは約 0.01 秒\) ごとにプロファイル情報が収集されます。  サンプリング メソッドはプロセッサ使用率の問題を検出するのに役立ち、ほとんどのパフォーマンス調査を開始するときに推奨される方法です。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
 サンプリング メソッドは、次のいずれかの手順で指定できます。  
  
-   プロファイル ウィザードの最初のページで、**\[CPU サンプリング \(推奨\)\]** をクリックします。  
  
-   **パフォーマンス エクスプローラー**のツール バーで、**\[メソッド\]** ボックスの一覧の **\[サンプリング\]** をクリックします。  
  
-   パフォーマンス セッションのプロパティ ダイアログ ボックスの **\[全般\]** ページで、**\[サンプリング\]** をクリックします。  
  
## 一般的なタスク  
 パフォーマンス セッションの *Performance Session***\[プロパティ ページ\]** ダイアログ ボックスで追加のオプションを指定できます。  このダイアログ ボックスを開くには、次の操作を行います。  
  
-   **パフォーマンス エクスプローラー**で、パフォーマンス セッション名を右クリックし、**\[プロパティ\]** をクリックします。  
  
 次の表のタスクは、サンプリング メソッドを使用してプロファイリングを実行するときに *Performance Session***\[プロパティ ページ\]** ダイアログ ボックスで指定できるオプションについて説明します。  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**\[全般\]** ページで、.NET メモリ割り当ておよび有効期間データの収集を追加し、生成されるプロファイル データ \(.vsp\) ファイルの名前付けの詳細を指定します。|-   [.NET メモリの割り当ておよび有効期間データの収集](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [方法: プロファイル データ ファイル名のオプションを設定する](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**\[サンプリング\]** ページで、サンプリング レートを変更するか、サンプリング イベントをプロセッサのクロック サイクルからプロセッサの別のパフォーマンス カウンターに変更するか、またはその両方を行います。|-   [方法 : サンプリング イベントを選択する](../Topic/How%20to:%20Choose%20Sampling%20Events.md)|  
|コード ソリューション内に複数の .exe プロジェクトがある場合は、**\[起動\]** ページで、開始するアプリケーションおよび開始順序を指定します。|-   [階層相互作用データの収集](../profiling/collecting-tier-interaction-data.md)|  
|**\[階層の相互作用\]** ページで、プロファイリング実行で収集されるデータに ADO.NET の呼び出しの情報を追加します。|-   [階層相互作用データの収集](../profiling/collecting-tier-interaction-data.md)|  
|**\[Windows イベント\]** ページで、サンプリング データと共に収集する 1 つ以上の ETW \(Event Tracing for Windows\) イベントを指定します。|-   [方法: ETW \(Event Tracing for Windows\) データを収集する](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|**\[Windows カウンター\]** ページで、プロファイル データにマークとして追加するオペレーティング システムのパフォーマンス カウンターを 1 つ以上指定します。|-   [方法 : Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)|  
|アプリケーション モジュールが複数バージョンの .NET Framework ランタイムを使用する場合、**\[詳細\]** ページで、プロファイルする .NET Framework ランタイム バージョンを指定します。  既定では、最初に読み込まれたバージョンがプロファイリングされます。|-   [方法: side\-by\-side 実行でプロファイリングするように .NET Framework ランタイムを指定する](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|