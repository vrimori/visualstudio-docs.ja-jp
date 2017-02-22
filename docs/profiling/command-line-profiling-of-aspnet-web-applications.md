---
title: "ASP.NET Web アプリケーションのコマンド ライン プロファイリング | Microsoft Docs"
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
  - "プロファイリング (ASP.NET アプリケーションを)"
  - "プロファイル ツール、ASP.NET アプリケーション"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ASP.NET Web アプリケーションのコマンド ライン プロファイリング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、コマンド ラインから [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールを使用して [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションのパフォーマンス データを収集する手順とオプションについて説明します。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**基本的な ASP.NET プロファイリング データの簡単な収集:  VSPerfASPNETCmd** ツールを使用して、サンプリング、インストルメンテーション、.NET メモリ、競合、または階層相互作用データを収集します。**VSPerfCmd** に必要な構成要件とインターネット インフォメーション サービス \(IIS\) の再起動は必要ありません。  **VSPerfASPNETCmd** では、追加のデータを収集したり、データ収集を制御することはできません。 **Note:**  **VSPerfASPNETCmd** は、スタンドアロン プロファイラーを使用して ASP.NET Web サイトのプロファイリングを行うときに推奨されるツールです。|-   [VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**アプリケーションの統計情報の収集:** サンプリング メソッドを使用してパフォーマンス統計情報を収集します。  サンプリング データは、CPU の使用率に関する問題の分析や、アプリケーションの全般的なパフォーマンス特性の把握に役立ちます。|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**詳細なタイミング データの収集:** インストルメンテーション メソッドを使用して詳細なタイミング データを収集します。  インストルメンテーション データは、IO に関する問題の分析や、アプリケーションのシナリオの詳細な分析に役立ちます。|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**.NET のメモリ データの収集:** サンプリング メソッドまたはインストルメンテーション メソッドを使用して、.NET のメモリの割り当てデータを収集し、割り当てられたオブジェクトのサイズと数を調べます。  オブジェクトの有効期間データを収集して、ガベージ コレクションが生成されるたびに、解放されたオブジェクトのサイズと数を調べることもできます。|-   [メモリ データの収集](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**同時実行データの収集:** 同時実行メソッドを使用してリソースの競合データを収集します。 **Note:**  スレッド アクティビティと視覚化データの収集は、Web アプリケーションではサポートされません。|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**階層相互作用データの追加:**  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションが Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] データベースに対して行う同期 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 呼び出しに関するパフォーマンス データを追加できます。|-   [階層相互作用データの収集](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 関連するタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**スタンドアロン \(クライアント\) アプリケーションをプロファイリングする**|-   [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**サービスをプロファイリングする**|-   [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)|