---
title: "方法: 収集方法を選択する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b94b842566c3f8bf5ad5374acda0ccc9e9b50cbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-choose-collection-methods"></a>方法: 収集方法を選択する
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールでは、サンプリング、インストルメンテーション、同時実行という 3 種類のパフォーマンス データ収集方法をサポートしています。 また、.NET メモリ割り当てと有効期間データの収集には、サンプリングまたはインストルメンテーションの方式を使用できます。  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 パフォーマンス セッションの **[メソッド]** プロパティを使用すると、アプリケーションに最適の収集方法を指定できます。 収集方法はパフォーマンス ウィザード、パフォーマンス エクスプローラー、またはパフォーマンス セッションのプロパティ ページから設定することができます。 コマンド ライン ツールを使用する場合、詳細については「[コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)」を参照してください。  
  
## <a name="performance-wizard"></a>パフォーマンス ウィザード  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>パフォーマンス ウィザードを使用して収集方法を選択するには  
  
-   ウィザードの最初のページで、次のいずれかのオプションを選択します。  
  
|オプション|説明|  
|------------|-----------------|  
|**CPU サンプリング**|初期の分析と CPU 使用率の問題の分析に役立つアプリケーション統計情報を収集します。|  
|**インストルメンテーション**|焦点を絞った分析、および入出力パフォーマンスの問題分析に役立つ詳しいタイミング データを収集します。|  
|**.NET メモリ割り当て**|サンプリング プロファイリング方式を使用して [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] メモリ割り当てデータを収集します。|  
|**同時実行**|数値のリソース競合データを収集します。|  
  
## <a name="performance-explorer"></a>パフォーマンス エクスプローラー  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>パフォーマンス エクスプローラーを使用して収集方法を選択するには  
  
1.  **パフォーマンス エクスプローラー**のツール バーで、**[メソッド]** ドロップダウン リストの横の矢印をクリックします。  
  
2.  必要な収集方法をクリックします。  
  
## <a name="performance-session-property-pages"></a>パフォーマンス セッションのプロパティ ページ  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>パフォーマンス セッションのプロパティを使用して、サンプリング方式またはインストルメンテーション方式を選択するには  
  
1.  **パフォーマンス エクスプローラー**でパフォーマンス セッションを選択します。  
  
     パフォーマンス セッション ファイル名の拡張子は .psess です。  
  
2.  パフォーマンス セッションを右クリックして、**[プロパティ]** をクリックします。  
  
3.  **[プロパティ ページ]** で **[全般]** をクリックします。  
  
4.  必要な収集方法をクリックします。  
  
    -   サンプリング データの収集に使用できるその他のオプションについては、「[サンプリングを使用したパフォーマンス統計情報の収集](../profiling/collecting-performance-statistics-by-using-sampling.md)」を参照してください。  
  
    -   サンプリング データの収集に使用できるその他のオプションについては、「[インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)」を参照してください。  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>パフォーマンス セッションのプロパティを使用して .NET メモリ データの収集を選択するには  
  
1.  **パフォーマンス エクスプローラー**でパフォーマンス セッションを選択します。  
  
     パフォーマンス セッション ファイル名の拡張子は .psess です。  
  
2.  パフォーマンス セッションを右クリックして、**[プロパティ]** をクリックします。  
  
3.  **[プロパティ ページ]** で **[全般]** をクリックします。  
  
4.  **[サンプリング]** または **[インストルメンテーション]** をクリックします。  
  
5.  **[.NET オブジェクトの割り当て情報を収集]** をクリックして [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] オブジェクト割り当てのサイズと数を収集します。  
  
6.  (省略可能) **[.NET オブジェクトの有効期間情報も収集]** をクリックして、オブジェクト メモリが解放されたガベージ コレクションの生成に関するデータを収集します。  
  
     .NET メモリ データの収集に使用できるその他のオプションについては、「[.NET メモリの割り当ておよび有効期間データの収集](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)」を参照してください。  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>パフォーマンス セッションのプロパティを使用して同時実行データの収集を選択するには  
  
1.  **パフォーマンス エクスプローラー**で、パフォーマンス セッションを右クリックして、 **[プロパティ]**をクリックします。  
  
2.  **[プロパティ ページ]** で **[全般]** をクリックします。  
  
3.  **[同時実行]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [サンプリング データ値について](../profiling/understanding-sampling-data-values.md)   
 [パフォーマンス セッションのプロパティ](../profiling/performance-session-properties.md)