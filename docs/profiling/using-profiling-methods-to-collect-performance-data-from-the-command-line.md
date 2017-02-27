---
title: "各種のプロファイル方法を使用したコマンド ラインからのパフォーマンス データの収集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 各種のプロファイル方法を使用したコマンド ラインからのパフォーマンス データの収集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用する [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールおよびオプションは、プロファイル対象のアプリケーションの種類、使用するプロファイル方法、ターゲット アプリケーションが、ネイティブ コードと [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] コードのどちらで記述されているかなどの要因によって決まります。  
  
 ここでは、コマンド ラインの手順について、使用するプロファイル方法ごとに説明します。  
  
## このトピックの内容  
 [サンプリング メソッドを使用してパフォーマンス統計情報を収集する](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [インストルメンテーション メソッドを使用して詳細なタイミング データを収集する](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [.NET メモリ メソッドを使用してメモリの割り当てとオブジェクトの有効期間のデータを収集する](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [同時実行メソッドを使用してリソースの競合およびスレッド アクティビティのデータを収集する](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [プロファイリングの実行に階層の相互作用データを追加する](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> サンプリング メソッドを使用してパフォーマンス統計情報を収集する  
 プロファイリング ツールのサンプリング メソッドでは、プロファイリングの実行中、指定した間隔でパフォーマンス データを収集します。  サンプリング データは、CPU 制約によるパフォーマンス上の問題を把握するのに役立ち、アプリケーションのパフォーマンスを調べるための最初の方法として適しています。  
  
 プロファイラーとアプリケーションを同時に開始することも、実行中のアプリケーションのインスタンスにプロファイラーをアタッチすることもできます。  
  
|タスク|ターゲット アプリケーションの種類|  
|---------|-----------------------|  
|**アプリケーションを起動する**|-   [スタンドアロン アプリケーション](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**実行中のプロセスにアタッチする**|-   [スタンドアロンの .NET Framework アプリケーション](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [スタンドアロンのネイティブ アプリケーション](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)<br />-   [ASP.NET Web アプリケーション](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET サービス](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [ネイティブ サービス](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> インストルメンテーション メソッドを使用して詳細なタイミング データを収集する  
 プロファイリング ツールのインストルメンテーション メソッドでは、パフォーマンス情報を記録するためのソフトウェア プローブを含むアプリケーション バイナリのコピーからパフォーマンス データを収集します。  インストルメント化された各関数の開始時と終了時、およびインストルメント化された関数から他の関数を呼び出すたびに、インストルメンテーション データが収集されます。  インストルメンテーション メソッドは、ディスクの使用率などの I\/O の問題に関連するパフォーマンス上の問題を検出するのに役立ちます。  
  
 [VInstr.exe](../profiling/vsinstr.md) ツールを使用すると、インストルメント化されたバイナリを作成できます。  プロファイラーを初期化すると、ターゲット アプリケーションの実行時にインストルメント化されたバイナリからデータが自動的に収集されます。  
  
 **ターゲット アプリケーションの種類**  
  
-   [スタンドアロンの .NET Framework コンポーネント](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [スタンドアロンのネイティブ コンポーネント](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [静的にコンパイルされた ASP.NET Web アプリケーション](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [動的にコンパイルされた ASP.NET Web アプリケーション](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)  
  
-   [.NET サービス](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [ネイティブ サービス](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> .NET メモリ メソッドを使用してメモリの割り当てとオブジェクトの有効期間のデータを収集する  
 プロファイリング ツールの .NET メモリ メソッドを使用すると、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] メモリの割り当ておよび [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のオブジェクトの有効期間に関する情報を収集できます。  
  
 プロファイラーを使用してターゲット アプリケーションを開始できるほか、実行中のアプリケーションのインスタンスにプロファイラーをアタッチすることもできます。[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] メモリ データと共に詳細なタイミング情報を収集するためのインストルメント化された形式のアプリケーションを作成することもできます。  
  
|タスク|ターゲット アプリケーションの種類|  
|---------|-----------------------|  
|**アプリケーションを起動する**|-   [スタンドアロンの .NET Framework アプリケーション](../Topic/How%20to:%20Launch%20a%20Stand-Alone%20.NET%20Framework%20Application%20with%20the%20Profiler%20to%20Collect%20Memory%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**実行中のプロセスにアタッチする**|-   [スタンドアロンの .NET Framework アプリケーション](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET Web アプリケーション](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET サービス](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**モジュールをインストルメント化する**|-   [スタンドアロンの .NET Framework コンポーネント](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [静的にコンパイルされた ASP.NET Web アプリケーション](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [動的にコンパイルされた ASP.NET Web アプリケーション](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET サービス](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> 同時実行メソッドを使用してリソースの競合およびスレッド アクティビティのデータを収集する  
 プロファイリング ツールの同時実行メソッドを使用すると、マルチスレッド アプリケーションのリソースの競合およびスレッドとプロセスのアクティビティ データを収集できます。  
  
 プロファイラーを使用してアプリケーションを開始することも、実行中のアプリケーションのインスタンスにプロファイラーをアタッチすることもできます。  
  
|タスク|ターゲット アプリケーションの種類|  
|---------|-----------------------|  
|**アプリケーションを起動する**|-   [スタンドアロンの .NET Framework アプリケーション](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [スタンドアロンのネイティブ アプリケーション](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**実行中のプロセスにアタッチする**|-   [スタンドアロンの .NET Framework アプリケーション](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [スタンドアロンのネイティブ アプリケーション](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [ASP.NET Web アプリケーション](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET サービス](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [ネイティブ サービス](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> プロファイリングの実行に階層の相互作用データを追加する  
 プロファイリングの実行に階層の相互作用データを追加するには、コマンド ライン プロファイリング ツールによる特定の手順が必要です。  「[階層相互作用データの収集](../profiling/adding-tier-interaction-data-from-the-command-line.md)」を参照してください。  
  
## 参照  
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)