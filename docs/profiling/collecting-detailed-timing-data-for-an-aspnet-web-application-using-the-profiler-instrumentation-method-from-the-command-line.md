---
title: "コマンド ラインからのプロファイラーのインストルメンテーション メソッドを使用した ASP.NET Web アプリケーションの詳細なタイミング データの収集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インストルメンテーション プロファイリング メソッド"
  - "プロファイル ツール, インストルメンテーション メソッド"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# コマンド ラインからのプロファイラーのインストルメンテーション メソッドを使用した ASP.NET Web アプリケーションの詳細なタイミング データの収集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、**VSPerfCmd** コマンド ライン ツールとインストルメンテーション メソッドを使用して [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションの詳細なパフォーマンス データを収集するための手順およびオプションを説明します。  
  
> [!NOTE]
>  **VSPerfCmd** ツールを使用すると、プロファイリング ツールの機能すべて \(プロファイリングの一時停止と再開、プロセッサおよび Windows パフォーマンス カウンターからの追加データの収集など\) にアクセスできます。  この機能が必要ない場合は、**VSPerfASPNETCmd** コマンド ライン ツールも使用できます。  [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールに比べると、環境変数を設定する必要がなく、コンピューターの再起動も必要ありません。  詳細については、「[VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)」を参照してください。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**静的にコンパイルしたバイナリをプロファイリングする**|-   [方法: 静的にコンパイルされた ASP.NET アプリケーションをインストルメントし、詳細なタイミング データを収集する](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**動的にコンパイルしたバイナリをプロファイリングする**|-   [方法: 動的にコンパイルされた ASP.NET アプリケーションをインストルメントし、詳細なタイミング データを収集する](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## 関連するタスク  
  
### ASP.NET Web アプリケーションのプロファイリング  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**サンプリング メソッドを使用してプロファイリングする**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**メモリの割り当ておよびガベージ コレクションをプロファイリングする**|-   [メモリ データの収集](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**リソースの競合およびスレッド アクティビティをプロファイリングする**|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### インストルメンテーション方式を使用したプロファイリング  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**スタンドアロン \(クライアント\) アプリケーションをプロファイリングする**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**サービスをプロファイリングする**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### インストルメンテーション データ ビューおよびレポートの分析  
 [インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)