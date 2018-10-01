---
title: パフォーマンス エクスプローラー | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance
- vs.performance.wizard.website
helpviewer_keywords:
- performance tools [Visual Studio ALM]
ms.assetid: df52b717-a55d-4b1d-8c2e-d5a6a38042f4
caps.latest.revision: 50
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2076aaa86f51da7928b0f81213ff97553262eb56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533615"
---
# <a name="performance-explorer"></a>パフォーマンス エクスプローラー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[パフォーマンス エクスプ ローラー](https://docs.microsoft.com/visualstudio/profiling/performance-explorer)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールによって、開発者は、コード内のパフォーマンス関連の問題を計測、評価、および特定することができます。 これらのツールは IDE に完全に統合されており、シームレスでわかりやすいユーザー エクスペリエンスを提供します。  
  
 アプリケーションのプロファイリングは簡単です。 新しいパフォーマンス セッションを作成することによって開始します。 Visual Studio Team System Development Edition では、パフォーマンス セッション ウィザードを使用して新しいパフォーマンス セッションを作成できます。 パフォーマンス セッション終了後、プロファイリング中に収集されたデータが .vsp ファイルに保存されます。 .vsp ファイルは IDE 内で参照できます。 いくつかのレポート ビューを使用して、収集したデータからパフォーマンス上の問題を視覚化し、検出できます。  
  
 プロファイリング ツールはコマンド ラインからも使用できます。 必要に応じて、パフォーマンス ツールをコマンド ラインから実行したり、スクリプトを使うタスクをパフォーマンス ツールによって自動化したりできます。  
  
 パフォーマンスおよびプロファイリングに関する最新トピックや高度なトピックの詳細については、Microsoft Developer Network や Microsoft ブログを検索してください。 キーワードには、"Enterprise Performance Tools Team" を指定してください。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**Windows 8 向けの新しい手法**|[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|  
|**プロファイリングの概念を理解する:** プロファイリング ツールを使用してコード パフォーマンスの収集、表示、分析を行う場合の概念と用語について説明します。|[概要](../profiling/overviews-performance-tools.md)|  
|**操作を行う:** プロファイリング ツールを使用してコード パフォーマンスの収集、表示、分析を行う場合に使用する基本的な手順について説明します。 チュートリアルに従って操作します。|[はじめに](../profiling/getting-started-with-performance-tools.md)|  
|**プロファイリング セッションを構成する:** プロファイリングを行うプロジェクトまたはバイナリを指定する方法、プロファイリング方式を選択する方法、収集するパフォーマンス データを選択する方法、およびその他のプロファイリング セッションのオプションを設定する方法の詳細について説明します。|[パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)|  
|**プロファイラーが収集するデータを制御する:** パフォーマンス セッションのプロパティおよび対話形式の手順を使用してプロファイリングを開始および停止する方法と、収集するパフォーマンス データを必要な情報だけに制限する方法について説明します。|[データ コレクションの制御](../profiling/controlling-data-collection.md)|  
|**パフォーマンスの問題を特定する:** 収集したパフォーマンス データをプロファイリング ツールのレポート ビュー ウィンドウに表示して分析する方法について説明します。|[パフォーマンス ツール データの分析](../profiling/analyzing-performance-tools-data.md)|  
|**パフォーマンスの変化を分析する:** 2 つのプロファイラー データ ファイルを比較して、パフォーマンスの変化を分析する方法について説明します。|[パフォーマンス データ ファイルの比較](../profiling/comparing-performance-data-files.md)|  
|**結果を保存して共有する:** プロファイリング データを保存してアーカイブまたは共有する方法について説明します。|[パフォーマンス ツール データの保存とエクスポート](../profiling/saving-and-exporting-performance-tools-data.md)|  
|**プロファイリングを自動化する:** コマンド プロンプトからプロファイリング ツールを使用する方法について説明します。|[コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)|  
|**プロファイリングをプログラムで制御する:** プロファイリング ツールのマネージド API とネイティブ API を使用して、ソース コードから直接データ コレクションを制御する方法について説明します。|[プロファイリング ツールの API](../profiling/profiling-tools-apis.md)|  
|**プロファイリングに関する問題のトラブルシューティング**|[パフォーマンス ツールに関する問題のトラブルシューティング](../profiling/troubleshooting-performance-tools-issues.md)|  
  
## <a name="see-also"></a>関連項目  
 [プロファイリング ツール](../profiling/profiling-tools.md)



