---
title: "プロファイラーのコマンド ラインを使用した ASP.NET Web アプリケーションからのメモリ データの収集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET メモリ プロファイル方法"
  - "プロファイル ツール, .NET メモリ方式"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プロファイラーのコマンド ラインを使用した ASP.NET Web アプリケーションからのメモリ データの収集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、**VSPerfCmd** のコマンド ライン ツールを使用して ASP.NET Web アプリケーションのメモリの割り当ておよびオブジェクトの有効期間データを収集するための手順およびオプションを説明します。  
  
> [!NOTE]
>  **VSPerfCmd** ツールを使用すると、プロファイリング ツールの機能すべて \(プロファイリングの一時停止と再開、プロセッサおよび Windows パフォーマンス カウンターからの追加データの収集など\) にアクセスできます。  この機能が必要ない場合は、**VSPerfASPNETCmd** コマンド ライン ツールも使用できます。  [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールに比べると、環境変数を設定する必要がなく、コンピューターの再起動も必要ありません。  詳細については、「[VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)」を参照してください。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**プロファイラーを実行中の ASP.NET アプリケーションにアタッチする**|-   [方法: プロファイラーを ASP.NET Web アプリケーションにアタッチし、メモリ データを収集する](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**静的にコンパイルしたバイナリをインストルメントする**|-   [方法: 静的にコンパイルされた ASP.NET アプリケーションをインストルメントし、メモリ データを収集する](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**動的にコンパイルしたバイナリをインストルメントする**|-   [方法: 動的にコンパイルされた ASP.NET アプリケーションをインストルメントし、メモリ データを収集する](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## 関連するタスク  
  
### ASP.NET Web アプリケーションのプロファイリング  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**サンプリング メソッドを使用してプロファイリングする**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**インストルメンテーション メソッドを使用してプロファイリングする**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**リソースの競合およびスレッド アクティビティをプロファイリングする**|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### .NET Framework メモリ データのプロファイリング  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**スタンドアロン \(クライアント\) アプリケーションをプロファイリングする**|-   [.NET Framework メモリ データの収集](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**サービスをプロファイリングする**|-   [.NET メモリ データの収集](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### .NET メモリ データ ビューおよびレポートの分析  
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md)  
  
## 参照  
 [コマンド ライン プロファイリング ツール リファレンス](../profiling/command-line-profiling-tools-reference.md)