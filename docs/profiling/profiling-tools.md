---
title: "プロファイリング ツール | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.diagnosticshub.overview"
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プロファイリング ツール
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロファイリングと診断のツールを利用すれば、メモリの利用状況、CPU の利用状況、その他のアプリケーション レベルの問題を診断できます。 これらのツールでは、デバッガーでアプリケーションを実行し、一定期間のデータを集めることができます \(変数値、関数呼び出し、イベントなど\)。 コードの実行中のさまざまな時点におけるアプリケーションの状態を表示できます。  
  
 一番下の概要を見ると、ある種類のプロジェクトで利用できるツールを確認できます \(デスクトップ、UWP、ASP.NET など\)。  
  
 プロファイリング ツールには次の方法でアクセスできます。デバッグ セッション中にツールを利用するには、**\[デバッグ\]、\[Windows\]、\[診断ツールの表示\]** の順に選択します。重点的なパフォーマンス分析を行うには、**\[デバッグ\]、\[パフォーマンス プロファイラー...\]** の順に選択します。 各種手法の詳細については、「[Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)」を参照してください。  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 このリリースの新機能の詳細については、「[診断ツールの新機能](../profiling/what-s-new-in-profiling-tools.md)」を参照してください。  
  
 次のセクションでは、Visual Studio で利用できるさまざまなパフォーマンス ツールについて説明します。  
  
## メモリ使用量  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 **メモリ使用量**ツールを使用したデバッグ中に、メモリ リークおよび非効率的なメモリを見つけます。 このツールを使用すると、マネージ メモリ ヒープとネイティブ メモリ ヒープのスナップショットを取得できます。 このツールはデスクトップ アプリ、Windows ユニバーサル アプリ、ASP.NET アプリで使用できます。**メモリ使用量**ツールは、デバッグ中に **\[診断ツール\]** ウィンドウから \(**\[デバッグ\]、\[Windows\]、\[診断ツールの表示\]**\)、またはデバッガーの外部で \(**\[デバッグ\]、\[パフォーマンス プロファイラー...\]**\) 実行できます。 詳細については、「[メモリ使用量](../profiling/memory-usage.md)」および「[デバッグなしのメモリ使用量の分析](../Topic/Memory%20Usage%20without%20Debugging1.md)」を参照してください。  
  
## CPU 使用率  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **CPU 使用率**ツールは、CPU が C\+\+、C\#\/VB、および JavaScript のコードを実行する際、どこで時間を費やしているかを示します。  このツールはデスクトップ、Windows ユニバーサル アプリ、Azure App Services アプリで使用できます。**CPU 使用量**ツールは、デバッグ中に **\[診断ツール\]** ウィンドウから \(**\[デバッグ\]、\[Windows\]、\[診断ツールの表示\]**\)、またはデバッガーの外部で \(**\[デバッグ\]、\[パフォーマンス プロファイラー...\]**\) 実行できます。 詳細については、「[CPU 使用率の分析](../profiling/cpu-usage.md)」を参照してください。  
  
## パフォーマンス エクスプローラー  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **パフォーマンス エクスプローラー**では \(**\[デバッグ\]、\[プロファイラー\]、\[パフォーマンス エクスプローラー\]**\)、**CPU サンプリング**、**インストルメンテーション**、**.NET メモリ割り当て**、**リソース競合**など、さまざまなツールを利用できます。 パフォーマンス エクスプローラーはデスクトップと ASP.NET アプリで使用できますが、Windows ユニバーサル アプリでは使用できません。 詳細については、「[プロファイリング ツールの使用](../profiling/performance-explorer.md)」を参照してください。  
  
## GPU 使用率  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 [GPU 使用率](../debugger/gpu-usage.md)ツールを利用すれば、Direct3D アプリの高いレベルのハードウェア使用率をより良く理解できます。 このツールはデスクトップ アプリと Windows ユニバーサル アプリで使用できますが、ASP.NET アプリでは使用できません。**GPU 使用量**ツールは、デバッグ中に **\[診断ツール\]** ウィンドウから \(**\[デバッグ\]、\[診断ツールの表示\]**\)、またはデバッガーの外部で \(**\[デバッグ\]、\[パフォーマンス プロファイラー...\]**\) 実行できます。  
  
## アプリケーションのタイムライン  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [アプリケーションのタイムライン](../profiling/application-timeline.md) ツールは XAML アプリケーションのリソース消費量の詳細を表示します。XAML アプリケーションのパフォーマンスの向上に役立ちます。**アプリケーションのタイムライン**はデスクトップ アプリと Windows ユニバーサル アプリで使用できますが、ASP.NET アプリでは使用できません。**アプリケーションのタイムライン** ツールは **\[診断ツール\]** ウィンドウから実行できます \(**\[デバッグ\]、\[パフォーマンス プロファイラー...\]**\)。  
  
## パフォーマンスのヒント  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 デバッガーがブレークポイントで実行を停止するか、ステップ実行を停止した場合、エディター ウィンドウに、ヒントとして前のブレークポイントからその中断までの経過時間が表示されます。 これらの [デバッガーでのパフォーマンス分析](../profiling/perftips.md) を利用すると、デバッグ中にアプリのパフォーマンスを監視し、分析できます。**PerfTips** はデスクトップ、Windows ユニバーサル、ASP.NET アプリに表示されます。  
  
## JavaScript メモリ  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [JavaScript メモリ](../profiling/javascript-memory.md)ツールでは、コードのパフォーマンス関連の問題を測定したり、評価したり、対象に設定したりできます。具体的には、アプリにおける各関数の開始と終了のタイミング情報を集めます。 このツールは Windows ユニバーサル HTML アプリで使用できます。**JavaScript 関数タイミング** ツールは **\[診断ツール\]** ウィンドウから実行できます \(**\[デバッグ\]、\[パフォーマンス プロファイラー...\]**\)。  
  
## HTML UI の応答性  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI の応答性](../profiling/html-ui-responsiveness.md) ツールを利用すれば、アプリにおける、応答がない、読み込み時間が遅い、表示の更新頻度が予想より少ないなどのパフォーマンス問題を分離できます。 このツールは Windows ユニバーサル HTML アプリで使用できます。**HTML UI の応答性**ツールは **\[診断ツール\]** ウィンドウから実行できます \(**\[デバッグ\]、\[パフォーマンス プロファイラー...\]**\)。  
  
## IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace の使用](../debugger/intellitrace.md) では、特定のイベントを記録したり、デバッガー イベントや関数呼び出しの間に **\[ローカル\]** ウィンドウでデータを調べたり、再現が難しいエラーをデバッグしたりできます。  IntelliTrace は主にデバッグ ツールですが、パフォーマンス調査に利用できる情報も提供します。 このツールはデスクトップ、Windows ユニバーサル、ASP.NET C\# アプリで使用できますが、Visual Studio Enterprise 専用です。 IntelliTrace にはデバッグ中に **\[診断ツール\]** ウィンドウからアクセスできます \(**\[デバッグ\]、\[Windows\]、\[診断ツールの表示\]**\)。  
  
## 実稼働のプロファイリング  
 実稼働プロファイリングの推奨方法は、[vsperf.exe を利用し、コマンド ライン](../profiling/using-the-profiling-tools-from-the-command-line.md)からプロファイリングし、CPU プロファイルを集めることです。 Azure App Service のリモート プロファイリング サポートの場合、[サーバー エクスプローラーまたは Kudu ポータル](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/)からプロファイルできます。  
  
## 使用するツール  
 次の表では、Visual Studio のさまざまなツールとそれらを使用できる各種プロジェクトをまとめています。  
  
|パフォーマンス ツール|Windows デスクトップ|Windows ユニバーサル\/ストア|ASP.NET|  
|-----------------|--------------------|-------------------------|-------------|  
|[メモリ使用量](../profiling/memory-usage.md)|可|可|no|  
|[CPU 使用率の分析](../profiling/cpu-usage.md)|可|可|Azure App Service のみ|  
|[GPU 使用率](../debugger/gpu-usage.md)|可|可|no|  
|[アプリケーションのタイムライン](../profiling/application-timeline.md)|可|可|no|  
|[デバッガーでのパフォーマンス分析](../profiling/perftips.md)|可|XAML の場合は可、HTML の場合は不可|no|  
|[プロファイリング ツールの使用](../profiling/performance-explorer.md)|可|no|可|  
|[IntelliTrace の使用](../debugger/intellitrace.md)|.NET Enterprise のみ|.NET Enterprise のみ|.NET Enterprise のみ|  
|[HTML UI の応答性](../profiling/html-ui-responsiveness.md)|no|HTML の場合は可、XAML の場合は不可|no|  
|[JavaScript メモリ](../profiling/javascript-memory.md)|no|HTML の場合は可、XAML の場合は不可|no|  
  
## 参照  
 [Visual Studio IDE](../ide/visual-studio-ide.md)