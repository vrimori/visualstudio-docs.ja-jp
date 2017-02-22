---
title: "スタンドアロン アプリケーションのコマンド ラインによるプロファイリング | Microsoft Docs"
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
  - "プロファイリング ツール、スタンドアロン アプリケーション"
  - "プロファイリング (スタンドアロン アプリケーションを)"
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# スタンドアロン アプリケーションのコマンド ラインによるプロファイリング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、コマンド ラインから [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールを使用して、スタンドアロン \(クライアント\) アプリケーションのパフォーマンス データを収集する手順とオプションについて説明します。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**アプリケーションの統計情報の収集:** サンプリング メソッドを使用してパフォーマンス統計情報を収集します。  サンプリング データは、CPU の使用率に関する問題の分析や、アプリケーションの全般的なパフォーマンス特性の把握に役立ちます。|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**詳細なタイミング データの収集:** インストルメンテーション メソッドを使用して詳細なタイミング データを収集します。  インストルメンテーション データは、I\/O に関する問題の分析や、アプリケーションのシナリオの詳細な分析に役立ちます。|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**.NET のメモリ データの収集:** サンプリング メソッドまたはインストルメンテーション メソッドを使用して、.NET のメモリの割り当てデータを収集し、割り当てられたオブジェクトのサイズと数を調べます。  オブジェクトの有効期間データを収集して、ガベージ コレクションが生成されるたびに、解放されたオブジェクトのサイズと数を調べることもできます。|-   [.NET Framework メモリ データの収集](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**同時実行データの収集:** 同時実行メソッドを使用して、リソースの競合データとスレッドのアクティビティ データを収集し、CPU 使用率、スレッドの競合、スレッドの移行、同期の遅延、重複 I\/O の領域などのシステム イベントを調べます。|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**階層相互作用データの追加:** アプリケーションが Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] データベースに対して行う同期 ADO.NET 呼び出しに関するパフォーマンス データを追加できます。  プロファイリングの実行に階層の相互作用データを追加するには、コマンド ライン プロファイリング ツールによる特定の手順が必要です。|-   [階層相互作用データの収集](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**テスト実行:** 操作手順に従って、サンプリング メソッドまたはインストルメンテーション メソッドでサンプルのクライアント アプリケーションをプロファイリングします。|-   [チュートリアル: サンプリングを使ったコマンド ライン プロファイリング](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)<br />-   [チュートリアル: インストルメンテーションを使ったコマンド ライン プロファイリング](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## 関連するタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**ASP.NET アプリケーションをプロファイリングする**|-   [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**サービスをプロファイリングする**|-   [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)|