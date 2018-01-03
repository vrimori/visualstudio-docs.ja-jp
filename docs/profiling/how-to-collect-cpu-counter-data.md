---
title: "方法: CPU カウンター データを収集する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 13bba809b77286cd4a6eea4efa41b69c317d23d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-collect-cpu-counter-data"></a>方法 : CPU カウンター データを収集する
CPU イベント カウンターはハードウェア固有のパフォーマンス データの収集に使用します。 このトピックでは、インストルメンテーション プロファイリング方式を使用した場合の、イベント カウンター データを収集する方法を示します。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 2 種類の CPU カウンター イベントが発生します。  
  
-   ポータブル イベント - 特定の CPU に関係なく、収集可能な CPU イベントです。  
  
-   プラットフォーム イベント - 特定の CPU に関連付けられた CPU イベントです。  
  
 ポータブル イベントには、Instructions Retired や Non Halted Cycles などの一般的なイベント、CPU バッファー イベント、分岐イベント、L2 キャッシュ イベントなどがあります。 使用できるプラットフォーム イベント カウンターはプロセッサの製造元によって決まります。  
  
 イベントのカテゴリは、ポータブル カウンターとプラットフォーム カウンターの間で共有できます。 たとえば、次のデータのカテゴリは、両方のタイプで一般的に共通するものです。  
  
-   メモリ イベント。  
  
-   フロントエンド イベント。  
  
-   分岐イベント。  
  
 プロファイラーでは、次の 2 つの方法でパフォーマンス カウンター データを収集できます。  
  
-   インストルメンテーションによってプロファイリングする場合は、1 つ以上のカウンターからデータを収集します。  
  
-   サンプリングによってプロファイリングする場合は、サンプリング間隔としてカウンター イベントを指定します。 詳細については、「[方法: サンプリング イベントを選択する](../profiling/how-to-choose-sampling-events.md)」を参照してください。  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>インストルメンテーションによってプロファイリングする場合に、CPU パフォーマンス カウンター データを収集するには  
  
1.  パフォーマンス セッションの **[プロパティ ページ]** で **[CPU カウンター]** をクリックします。  
  
2.  **[CPU カウンターの収集]** チェック ボックスをオンにします。  
  
3.  収集するサンプル イベントが見つかるまで、**[使用可能なパフォーマンス カウンター]** ツリーを展開します。  
  
4.  収集するそれぞれのイベントについて、イベントを選択して右矢印をクリックし、そのイベントを **[選択されたカウンター]** 一覧に追加します。  
  
    > [!NOTE]
    >  **[使用可能なパフォーマンス カウンター]** は、**[CPU カウンターの収集]** チェック ボックスがオンになっている場合のみ有効です。  
  
## <a name="see-also"></a>参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [パフォーマンス セッションのプロパティ](../profiling/performance-session-properties.md)   
 [CPU カウンターと Windows カウンター](../profiling/cpu-and-windows-counters.md)   
 [方法: サンプリング イベントを選択する](../profiling/how-to-choose-sampling-events.md)