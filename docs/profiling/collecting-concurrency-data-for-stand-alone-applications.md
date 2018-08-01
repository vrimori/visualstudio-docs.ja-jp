---
title: プロファイラーのコマンド ラインを使用したスタンドアロン アプリケーションの同時実行データの収集 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7966bcffff03c23b99837ba69f591d76258146c
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276482"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>プロファイラーのコマンド ラインを使用したスタンドアロン アプリケーションの同時実行データの収集
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールの同時実行メソッドを使用すると、リソース競合データとスレッド アクティビティ データを収集し、CPU 使用率、スレッド競合、スレッドの移行、同期の遅延、重複 I/O の領域などのシステム イベントを表示できます。  
  

## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連コンテンツ|  
|----------|---------------------|  
|**.NET Framework アプリケーションとプロファイル同時実行データの起動**|-   [方法: .NET Framework アプリケーションを起動し、同時実行データを収集する](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|  
|**C/C++ アプリケーションとプロファイル同時実行データの起動**|-   [方法: ネイティブ アプリケーションを起動し、同時実行データを収集する](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|  
|**実行中の .NET Framework アプリケーションにプロファイラーをアタッチする**|-   [方法: プロファイラーを .NET Framework アプリケーションにアタッチし、同時実行データを収集する](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|  
|**実行中の C/C++ アプリケーションにプロファイラーをアタッチする**|-   [方法: プロファイラーをネイティブ アプリケーションにアタッチし、同時実行データを収集する](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|  
  
## <a name="related-tasks"></a>関連するタスク
  
### <a name="profile-stand-alone-applications"></a>スタンドアロン アプリケーションのプロファイリング  
  
|タスク|関連コンテンツ|  
|----------|---------------------|  
|**サンプリング メソッドを使用したプロファイリング**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**インストルメンテーション方式を使用したプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**.NET のメモリ割り当てとガベージ コレクションのプロファイリング**|-   [.NET Framework メモリ データの収集](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**階層の相互作用データを追加する**|-   [階層相互作用データを収集する](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profile-concurrency-issues"></a>同時実行の問題のプロファイリング  
  
|タスク|関連コンテンツ|  
|----------|---------------------|  
|**ASP.NET アプリケーションのプロファイリング**|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
|**サービスのプロファイリング**|-   [同時実行データの収集](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyze-concurrency-data-views-and-reports"></a>同時実行データ ビューとレポートの分析  
 [リソース競合データのビュー](../profiling/resource-contention-data-views.md)  
  
 [同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>参照  
 [コマンド ライン プロファイリング ツール リファレンス](../profiling/command-line-profiling-tools-reference.md)