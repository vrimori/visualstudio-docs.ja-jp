---
title: "プロファイラーのコマンド ラインを使用したスタンドアロン アプリケーションの同時実行データの収集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91e079fa996c30160454dcd7f8cc3d3bade27b2d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>プロファイラーのコマンド ラインを使用したスタンドアロン アプリケーションの同時実行データの収集
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールの同時実行メソッドを使用すると、リソース競合データとスレッド アクティビティ データを収集し、CPU 使用率、スレッド競合、スレッドの移行、同期の遅延、重複 I/O の領域などのシステム イベントを表示できます。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連コンテンツ|  
|----------|---------------------|  
|**.NET Framework アプリケーションとプロファイル同時実行データの起動**|-   [方法: .NET Framework アプリケーションを起動し、同時実行データを収集する](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**C/C++ アプリケーションとプロファイル同時実行データの起動**|-   [方法: ネイティブ アプリケーションを起動し、同時実行データを収集する](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**実行中の .NET Framework アプリケーションにプロファイラーをアタッチする**|-   [方法: プロファイラーを .NET Framework アプリケーションにアタッチし、同時実行データを収集する](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**実行中の C/C++ アプリケーションにプロファイラーをアタッチする**|-   [方法: プロファイラーをネイティブ アプリケーションにアタッチし、同時実行データを収集する](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
### <a name="profiling-stand-alone-applications"></a>スタンドアロン アプリケーションのプロファイリング  
  
|タスク|関連コンテンツ|  
|----------|---------------------|  
|**サンプリング メソッドを使用したプロファイリング**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**インストルメンテーション方式を使用したプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**.NET のメモリ割り当てとガベージ コレクションのプロファイリング**|-   [.NET Framework メモリ データの収集](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**階層の相互作用データを追加する**|-   [階層相互作用データの収集](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>同時実行の問題  
  
|タスク|関連コンテンツ|  
|----------|---------------------|  
|**ASP.NET アプリケーションのプロファイリング**|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**サービスのプロファイリング**|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>同時実行データ ビューとレポートの分析  
 [リソース競合データのビュー](../profiling/resource-contention-data-views.md)  
  
 [同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>参照  
 [コマンド ライン プロファイリング ツール リファレンス](../profiling/command-line-profiling-tools-reference.md)