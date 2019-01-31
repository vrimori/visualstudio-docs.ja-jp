---
title: プロファイラー サンプリング メソッドを使用したサービスのアプリケーション統計情報の収集 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1de40418af63c3d5a963bd83a59c916c87251b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961586"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>プロファイラー サンプリング メソッドを使用したサービスのアプリケーション統計情報の収集
このセクションでは、コマンド ラインからサンプリング メソッドを使用して、Windows サービスのパフォーマンスの統計情報を収集する手順とオプションについて説明します。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 UWP アプリにも新しい収集手法が必要です。 「[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**プロファイラーを .NET サービスにアタッチする**|-   [方法: プロファイラーを .NET サービスにアタッチし、アプリケーションの統計情報を収集する](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**階層の相互作用データを追加する**|-   [階層相互作用データを収集する](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**プロファイラーを C/C++ サービスにアタッチする**|-   [方法: プロファイラーをネイティブ サービスにアタッチし、アプリケーションの統計情報を収集する](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>関連するタスク  
  
### <a name="profile-windows-services"></a>Windows サービスのプロファイリング  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**インストルメンテーション方式を使用したプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
|**.NET のメモリ割り当てとガベージ コレクションのプロファイリング**|-   [.NET メモリ データの収集](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**リソースの競合とスレッド アクティビティのプロファイリング**|-   [コンカレンシー データの収集](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  

### <a name="profile-by-using-the-sampling-method"></a>サンプリング メソッドを使用したプロファイリング  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**スタンドアロン (クライアント) アプリケーションのプロファイリング**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**ASP.NET Web アプリケーションのプロファイリング**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
  
### <a name="analyze-sampling-data-views-and-reports"></a>サンプリング データ ビューとレポートの分析  
 [サンプリング メソッドのデータ ビュー](../profiling/profiler-sampling-method-data-views.md)
