---
title: "Visual Studio のプロファイリング ツール | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 0d129b4820944f5717c63243cb8550bc4fed3385
ms.openlocfilehash: 380b65540d8f5c6ea6d8a8adf1f3c5575f5dd9dc
ms.lasthandoff: 03/20/2017

---
# <a name="profiling-tools"></a>プロファイリング ツール
プロファイリングと診断のツールを利用すれば、メモリの利用状況、CPU の利用状況、その他のアプリケーション レベルの問題を診断できます。 これらのツールでは、デバッガーでアプリケーションを実行し、一定期間のデータを集めることができます (変数値、関数呼び出し、イベントなど)。 コードの実行中のさまざまな時点におけるアプリケーションの状態を表示できます。  
  
 一番下の概要を見ると、ある種類のプロジェクトで利用できるツールを確認できます (デスクトップ、UWP、ASP.NET など)。  
  
 プロファイリング ツールには次の方法でアクセスできます。デバッグ セッション中にツールを利用するには、**[デバッグ]、[Windows]、[診断ツールの表示]** の順に選択します。重点的なパフォーマンス分析を行うには、[デバッグ]、[パフォーマンス プロファイラー...] の順に選択します。  各種手法の詳細については、「[Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)」(デバッガーを使用して、または使用せずにプロファイリング ツールを実行する) を参照してください。
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")
  
 このリリースの新機能の詳細については、「[診断ツールの新機能](../profiling/what-s-new-in-profiling-tools.md)」を参照してください。
  
 次のセクションでは、Visual Studio で利用できるさまざまなパフォーマンス ツールについて説明します。
  
## <a name="memory-usage"></a>メモリ使用量  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 **メモリ使用量** ツールを使用したデバッグ中に、メモリ リークおよび非効率的なメモリを見つけます。 このツールを使用すると、マネージ メモリ ヒープとネイティブ メモリ ヒープのスナップショットを取得できます。 このツールはデスクトップ アプリ、Windows ユニバーサル アプリ、ASP.NET アプリで使用できます。 **メモリ使用量** ツールは、デバッグ中に **[診断ツール]** ウィンドウから (**[デバッグ]、[Windows]、[診断ツールの表示]**)、またはデバッガーの外部で (**[デバッグ]、[パフォーマンス プロファイラー...]**) 実行できます。 詳細については、「[メモリ使用量](../profiling/memory-usage.md)」および「[デバッグなしのメモリ使用量の分析](../profiling/Memory-Usage-without-Debugging2.md)」を参照してください。  
  
## <a name="cpu-usage"></a>CPU 使用率  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **CPU 使用率** ツールは、CPU が C++、C#/VB、および JavaScript のコードを実行する際、どこで時間を費やしているかを示します。  このツールはデスクトップ、Windows ユニバーサル アプリ、ASP.NET アプリ、および Azure App Service アプリで使用できます。 **CPU 使用量** ツールは、デバッグ中に **[診断ツール]** ウィンドウから (**[デバッグ]、[Windows]、[診断ツールの表示]**)、またはデバッガーの外部で (**[デバッグ]、[パフォーマンス プロファイラー...]**) 実行できます。 詳細については、「[パフォーマンス プロファイリングのビギナーズ ガイド](../profiling/beginners-guide-to-performance-profiling.md)」および「[CPU 使用率](../profiling/cpu-usage.md)」を参照してください。
  
## <a name="gpu-usage"></a>GPU 使用率  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 [GPU Usage](../debugger/gpu-usage.md) ツールを利用すれば、Direct3D アプリの高いレベルのハードウェア使用率をより一層理解できます。 このツールはデスクトップ アプリと Windows ユニバーサル アプリで使用できますが、ASP.NET アプリでは使用できません。 **GPU 使用量**ツールは、デバッガーの外部 (**[デバッグ]、[パフォーマンス プロファイラー...]**) で実行できます。  
  
## <a name="application-timeline"></a>アプリケーションのタイムライン  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Application Timeline](../profiling/application-timeline.md) ツールは XAML アプリケーションのリソース消費量の詳細を表示します。XAML アプリケーションのパフォーマンスの向上に役立ちます。 **アプリケーションのタイムライン** はデスクトップ アプリと Windows ユニバーサル アプリで使用できますが、ASP.NET アプリでは使用できません。 **アプリケーションのタイムライン** ツールは、デバッガーの外部 (**[デバッグ]、[パフォーマンス プロファイラー...]**) で実行できます。
  
## <a name="perftips"></a>パフォーマンスのヒント  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 デバッガーがブレークポイントで実行を停止するか、ステップ実行を停止した場合、エディター ウィンドウに、ヒントとして前のブレークポイントからその中断までの経過時間が表示されます。 これらの [PerfTips](../profiling/perftips.md) を利用すると、デバッグ中にアプリのパフォーマンスを監視し、分析できます。 **PerfTips** はデスクトップ、Windows ユニバーサル、ASP.NET アプリに表示されます。

## <a name="performance-explorer"></a>パフォーマンス エクスプローラー  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **パフォーマンス エクスプローラー** では (**[デバッグ]、[プロファイラー]、[パフォーマンス エクスプローラー]**)、 **CPU サンプリング**、  **インストルメンテーション**、 **.NET メモリ割り当て**、 **リソース競合**など、さまざまなツールを利用できます。 パフォーマンス エクスプローラーはデスクトップと ASP.NET アプリで使用できますが、Windows ユニバーサル アプリでは使用できません。 詳細については、「[Performance Explorer](../profiling/performance-explorer.md)」(パフォーマンス エクスプローラー) を参照してください。

 > [!NOTE]
 > インストルメンテーションなどの特殊なタスクを実行する場合を除き、(レガシ ツールの) パフォーマンス エクスプローラーではなく、メモリ使用量や CPU 使用量などの診断ツールを使用してください。
  
## <a name="javascript-memory"></a>[JavaScript メモリ]  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [JavaScript メモリ](../profiling/javascript-memory.md) ツールを使用すると、アプリ内のメモリ リークおよび非効率的なメモリの使用を見つけられます。 このツールを使用すると、JavaScript ヒープのスナップショットを取得できます。 このツールは Windows ユニバーサル HTML アプリで使用できます。 **JavaScript メモリ** ツールは、デバッガーの外部 (**[デバッグ]、[パフォーマンス プロファイラー...]**) で実行できます。  
  
## <a name="html-ui-responsiveness"></a>HTML UI の応答性  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI responsiveness](../profiling/html-ui-responsiveness.md) ツールを利用すれば、アプリにおける、応答がない、読み込み時間が遅い、表示の更新頻度が予想より少ないなどのパフォーマンス問題を分離できます。 このツールは Windows ユニバーサル HTML アプリで使用できます。 **HTML UI の応答性**ツールは、デバッガーの外部 (**[デバッグ]、[パフォーマンス プロファイラー...]**) で実行できます。  
  
## <a name="intellitrace"></a>[IntelliTrace]  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) では、特定のイベントを記録したり、デバッガー イベントや関数呼び出しの間に **[ローカル]** ウィンドウでデータを調べたり、再現が難しいエラーをデバッグしたりできます。  IntelliTrace は主にデバッグ ツールですが、パフォーマンス調査に利用できる情報も提供します。 このツールはデスクトップ、Windows ユニバーサル、ASP.NET C# アプリで使用できますが、Visual Studio Enterprise 専用です。 IntelliTrace にはデバッグ中に **[診断ツール]** ウィンドウからアクセスできます (**[デバッグ]、[Windows]、[診断ツールの表示]**)。  
  
## <a name="profiling-in-production"></a>実稼働のプロファイリング  
 実稼働プロファイリングの推奨方法は、[vsperf.exe を利用し、コマンド ライン](../profiling/using-the-profiling-tools-from-the-command-line.md) からプロファイリングし、CPU プロファイルを集めることです。 Azure App Service のリモート プロファイリング サポートの場合、 [サーバー エクスプローラーまたは Kudu ポータル](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/)からプロファイルできます。  
  
## <a name="which-tool-should-i-use"></a>使用するツール  
 次の表では、Visual Studio のさまざまなツールとそれらを使用できる各種プロジェクトをまとめています。  
  
|パフォーマンス ツール|Windows デスクトップ|Windows ユニバーサル/ストア|ASP.NET/ASP.NET Core|  
|----------------------|---------------------|------------------------------|-------------|  
|[メモリ使用量](../profiling/memory-usage.md)|可|可|可|  
|[CPU 使用率](../profiling/cpu-usage.md)|可|可|可|  
|[GPU 使用率](../debugger/gpu-usage.md)|可|可|no|  
|[アプリケーションのタイムライン](../profiling/application-timeline.md)|可|可|no|  
|[パフォーマンスのヒント](../profiling/perftips.md)|可|XAML の場合は可、HTML の場合は不可|可|  
|[パフォーマンス エクスプローラー](../profiling/performance-explorer.md)|可|no|可 (ASP.NET Core の場合は no)|  
|[IntelliTrace](../debugger/intellitrace.md)|.NET Enterprise のみ|.NET Enterprise のみ|.NET Enterprise のみ|
|[ネットワーク使用率](../profiling/network-usage.md)|no|可|no| 
|[HTML UI の応答性](../profiling/html-ui-responsiveness.md)|no|HTML の場合は可、XAML の場合は不可|no|  
|[JavaScript メモリ](../profiling/javascript-memory.md)|no|HTML の場合は可、XAML の場合は不可|no|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
