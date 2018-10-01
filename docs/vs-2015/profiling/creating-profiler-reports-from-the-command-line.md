---
title: コマンド ラインからのプロファイラー レポートの作成 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d94a2c6c025ada73e1d43e041c2bf6e30f8b66c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536916"
---
# <a name="creating-profiler-reports-from-the-command-line"></a>コマンド ラインからのプロファイラー レポートの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コマンドラインから Profiler レポートを作成する](https://docs.microsoft.com/visualstudio/profiling/creating-profiler-reports-from-the-command-line)します。  
  
**VSPerfReport** コマンド ライン ツールを使用すると、プロファイル データ (.vsp) ファイルから .xml レポートまたはコンマ区切り値 (.csv) レポートを作成できます。 VSPerfReport のレポートの種類は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のインターフェイスのテーブル ベースのビューとほぼ同じです。 レポートをフィルター処理して、コードのみを表示したり、プロファイル データ ファイルのセグメントのみを表示したりできます。 詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
 また、.vsp ファイルにシンボルを埋め込んだり、サイズが小さく、すばやく開くことのできる解析済みレポート (.vsps) ファイルを作成することにより、プロファイル データ ファイルを簡単に共有できます。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**基本的なレポートを作成する。** VSPerfReport レポートのすべての種類またはサブセットを作成します。|-   [基本的なレポートの作成](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**2 つのプロファイル データ ファイルを比較する。** 2 つのプロファイル データ ファイルのパフォーマンス データを比較する "比較" レポートを作成します。|-   [方法: コマンド プロンプトからプロファイラー比較レポートを作成する](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**コール トレース データおよび ETW (Event Trace for Windows) データを表示する。** アプリケーションの関数に対する各エントリ ポイントと終了ポイント、および実行中の関数から他の関数に対する各呼び出しのタイミング情報を一覧表示するコール トレース レポートを作成します。 または、プロファイリング実行で収集されたすべての ETW イベントの詳細な一覧を作成します。|-   [方法: コール トレース レポートを作成する](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**レポートをフィルター処理する。** レポートの内容を、コード内の関数のみまたはプロファイル データ ファイル内の特定の時刻のみに制限します。|-   [方法: コマンド ラインからレポートをフィルター処理する](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**移植可能なプロファイル データ ファイルを作成する。** プロファイル データの共有を簡単に行うために、プロファイリング実行用のシンボルを .vsp ファイル内に埋め込むことができます。 また、サイズが小さく、すばやく開くことのできる解析済みプロファイル データ (.vsps) ファイルを作成することもできます。|-   [移植可能なプロファイル データ ファイルの作成](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|



