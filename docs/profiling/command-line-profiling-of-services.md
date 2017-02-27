---
title: "コマンド ライン プロファイリング (サービスの) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイリング ツール, サービス"
  - "プロファイリング (サービスの)"
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# コマンド ライン プロファイリング (サービスの)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、コマンド ラインから [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールを使用して Windows サービスのパフォーマンス データを収集する手順とオプションについて説明します。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**アプリケーションの統計情報の収集:** サンプリング メソッドを使用してパフォーマンス統計情報を収集します。  サンプリング データは、CPU の使用率に関する問題の分析や、アプリケーションの全般的なパフォーマンス特性の把握に役立ちます。|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**詳細なタイミング データの収集:** インストルメンテーション メソッドを使用して詳細なタイミング データを収集します。  インストルメンテーション データは、IO に関する問題の分析や、アプリケーションのシナリオの詳細な分析に役立ちます。|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**.NET のメモリ データの収集:** サンプリング メソッドまたはインストルメンテーション メソッドを使用して、.NET のメモリの割り当てデータを収集し、割り当てられたオブジェクトのサイズと数を調べます。  オブジェクトの有効期間データを収集して、ガベージ コレクションが生成されるたびに、解放されたオブジェクトのサイズと数を調べることもできます。|-   [.NET メモリ データの収集](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**同時実行データの収集:** 同時実行メソッドを使用して、リソースの競合データとスレッドのアクティビティ データを収集し、CPU 使用率、スレッドの競合、スレッドの移行、同期の遅延、重複 I\/O の領域などのシステム イベントを調べます。|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**階層相互作用データの追加:** サービスが Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] データベースに対して行う同期 ADO.NET 呼び出しに関するパフォーマンス データを追加できます。|-   [階層相互作用データの収集](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 関連するタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**スタンドアロン \(クライアント\) アプリケーションをプロファイリングする**|-   [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**ASP.NET アプリケーションをプロファイリングする**|-   [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)|