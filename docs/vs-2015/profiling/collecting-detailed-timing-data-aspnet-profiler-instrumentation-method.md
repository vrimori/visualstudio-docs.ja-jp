---
title: コマンド ラインからのプロファイラーのインストルメンテーション メソッドを使用した ASP.NET Web アプリケーションの詳細なタイミング データの収集 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eabd6d66079fc003bb87e867c0b5bb572c3bddc1
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592566"
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>コマンド ラインからのプロファイラーのインストルメンテーション メソッドを使用した ASP.NET Web アプリケーションの詳細なタイミング データの収集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[収集詳細なタイミング データを使用して ASP.NET Web アプリケーションのコマンドラインから Profiler インストルメンテーション メソッド](https://docs.microsoft.com/visualstudio/profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line)します。  
  
このセクションでは、**VSPerfCmd** コマンド ライン ツールとインストルメンテーション メソッドを使用して、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーションの詳細なパフォーマンス データを収集する手順とオプションについて説明します。  
  
> [!NOTE]
>  **VSPerfCmd** ツールを使用すると、すべてのプロファイル ツール機能にアクセスできます。たとえば、プロファイリングを一時停止したり、再開したり、プロセッサや Windows パフォーマンス カウンターから追加データを収集したりできます。 この機能が不要な場合、**VSPerfASPNETCmd** コマンドライン ツールも利用できます。 [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールと比較すると、環境変数を設定する必要がなく、コンピューターを再起動する必要がありません。 詳細については、「[VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)」を参照してください。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**静的にコンパイルされたバイナリをプロファイリングする**|-   [方法: 静的にコンパイルされた ASP.NET アプリケーションをインストルメント化し、詳細なタイミング データを収集する](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**動的にコンパイルされたバイナリをプロファイリングする**|-   [方法: 動的にコンパイルされた ASP.NET アプリケーションをインストルメント化し、詳細なタイミング データを収集する](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
### <a name="profiling-aspnet-web-applications"></a>ASP.NET Web アプリケーションのプロファイリング  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**サンプリング メソッドを使用したプロファイリング**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**メモリ割り当てとガベージ コレクションのプロファイリング**|-   [メモリ データの収集](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**リソースの競合とスレッド アクティビティのプロファイリング**|-   [コンカレンシー データの収集](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>インストルメンテーション方式を使用したプロファイリング  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**スタンドアロン (クライアント) アプリケーションのプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**サービスのプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>インストルメンテーション データ ビューとレポートの分析  
 [インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)



