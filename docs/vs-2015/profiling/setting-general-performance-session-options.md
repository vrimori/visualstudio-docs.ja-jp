---
title: パフォーマンス セッションの全般オプションの設定 | Microsoft Docs
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
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abf40be314191096447e389ef145385d2e0f616b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537912"
---
# <a name="setting-general-performance-session-options"></a>パフォーマンス セッションの全般オプションの設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[パフォーマンス セッションのオプションの [全般] 設定](https://docs.microsoft.com/visualstudio/profiling/setting-general-performance-session-options)します。  
  
パフォーマンス セッションのプロパティ ダイアログ ボックスの **[全般]** ページで、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイル ツールのパフォーマンス セッションに収集方法およびプロファイル データの名前付け規則を設定することができます。 **パフォーマンス エクスプローラー**からこのダイアログ ボックスを開くには、パフォーマンス セッションを右クリックし、**[プロパティ]** をクリックします。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>データ コレクション方法の選択  
 基本的な収集方法を設定するには、**[プロファイル コレクション]** でオプションのいずれかを選択します。 オプションは次の表のとおりです。  
  
|||  
|-|-|  
|**サンプリング**。 サンプリング メソッドでは、一定の間隔でプロファイル情報を収集します。 この方法はプロセッサ使用率の問題を検出するのに役立ち、ほとんどのパフォーマンス調査を開始するときに推奨される方法です。|-   [サンプリングを使用したパフォーマンス統計情報の収集](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**インストルメンテーション**。 インストルメンテーション メソッドでは、モジュールのコピーにプロファイル コードが挿入されます。このコードは、プロファイリング実行中のモジュール内の関数の開始、終了、および関数呼び出しをそれぞれ記録します。 この方法は、コード セクションに関する詳細なタイミング情報を収集し、アプリケーションのパフォーマンスに対する入出力操作の影響を理解するのに役立ちます。|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**コンカレンシー**。 コンカレンシー メソッドでは、アプリケーション リソースへのロックされたアクセスが解放されるまでスレッドが待機している場合など、コードの実行をブロックする各イベントのデータを収集します。 この方法は、マルチスレッド アプリケーションを分析するのに役立ちます。|-   [スレッドおよびプロセスのコンカレンシー データの収集](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 .NET メモリ データは、サンプリング メソッドまたはインストルメンテーション メソッドを使用して収集できます。 データの種類は **[.NET メモリ プロファイル]** で選択します。  
  
|||  
|-|-|  
|**.NET オブジェクトの割り当て情報を収集**。 既定では、割り当てられたオブジェクトの数とサイズがデータに含まれます。 .NET メモリ データの収集を有効または無効にするには、このチェック ボックスをオンまたはオフにします。<br /><br /> **.NET オブジェクトの有効期間情報も収集**。 メモリ オブジェクトを再利用するために使用されたガベージ コレクション ジェネレーションに関するデータを含めるには、このチェック ボックスをオンにします。|-   [.NET メモリの割り当ておよび有効期間データの収集](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 アプリケーションのプロファイリングを開始すると、プロファイル セッション ページが表示されます。このページで、プロファイリングを一時停止、再開、および停止することができます。  
  
 ![プロファイリング セッションのページ](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-datra-file-options"></a>プロファイル データ ファイルのオプションの設定  
  
|||  
|-|-|  
|**レポート**。 既定では、プロファイル データ (.vsp) ファイルはプロファイリング対象のアプリケーションの名前を割り当てられ、ソリューション フォルダーまたはプロジェクト フォルダーに配置されます。 その名前に、日付文字列も追加されます。さらに、データ ファイルの名前が重複する可能性がある場合は、インクリメントされた番号も追加されます。 これらのオプションは変更できます。|-   [方法: パフォーマンス データ ファイル名のオプションを設定する](../profiling/how-to-set-performance-data-file-name-options.md)|



