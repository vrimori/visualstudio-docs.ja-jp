---
title: "方法: インストルメンテーション方式を使用して CPU カウンター データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "プロファイリング ツール、使用 (移植性の高い CPU カウンターを)"
  - "パフォーマンス ツール、移植性の高い CPU カウンター"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法: インストルメンテーション方式を使用して CPU カウンター データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ハードウェア固有のパフォーマンス データの収集には、CPU イベント カウンターが使用されます。  このトピックでは、インストルメンテーションにメソッドを使用するときは、イベント カウンター データを収集する方法について説明します。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 次の 2 種類の CPU カウンター イベントが発生します。  
  
-   汎用性のあるイベント \- 特定の CPU にかかわらず収集可能な CPU イベント  
  
-   プラットフォーム イベント \- 特定の CPU に関連付けられた CPU イベント  
  
 汎用性のあるイベントには、Instructions Retired や Non Halted Cycles などの一般的なイベント、CPU バッファー イベント、分岐イベント、および L2 キャッシュ イベントが含まれます。  使用できるプラットフォーム イベント カウンターは、プロセッサのメーカーによって決められています。  
  
 イベントのカテゴリは、汎用性のあるカウンターとプラットフォーム カウンターで共有できます。  たとえば、両方のタイプに共通するデータのカテゴリには次のものがあります。  
  
-   メモリ イベント  
  
-   フロントエンド イベント  
  
-   分岐イベント  
  
 パフォーマンス カウンター データは、プロファイラーを使った次の 2 つの方法で収集できます。  
  
-   インストルメンテーションによってプロファイリングするときに 1 つ以上のカウンターからデータを収集する。  
  
-   サンプリングによってプロファイリングするときにカウンター イベントをサンプリング間隔として指定する。  詳細については、「[方法 : サンプリング イベントを選択する](../Topic/How%20to:%20Choose%20Sampling%20Events.md)」を参照してください。  
  
### インストルメンテーションによってプロファイリングをするときに CPU パフォーマンス カウンター データを収集するには  
  
1.  パフォーマンス セッションの **\[プロパティ ページ\]** で、**\[CPU カウンター\]** をクリックします。  
  
2.  **\[CPU カウンターの収集\]** チェック ボックスをオンにします。  
  
3.  **\[使用可能なパフォーマンス カウンター\]** ツリーを展開し、収集するサンプル イベントを見つけます。  
  
4.  収集するイベントごとに、イベントを選択して右矢印をクリックし、イベントを **\[選択されたカウンター\]** リストに追加します。  
  
    > [!NOTE]
    >  **\[使用可能なパフォーマンス カウンター\]** が有効になるのは **\[CPU カウンターの収集\]** チェック ボックスをオンにした場合だけです。  
  
## 参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [パフォーマンス セッションのプロパティ](../profiling/performance-session-properties.md)   
 [CPU カウンターと Windows カウンター](../profiling/cpu-and-windows-counters.md)   
 [方法 : サンプリング イベントを選択する](../Topic/How%20to:%20Choose%20Sampling%20Events.md)