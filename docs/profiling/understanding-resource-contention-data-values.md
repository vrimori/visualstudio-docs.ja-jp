---
title: "プロファイリング ツールのリソース競合データ値について | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "同時実行プロファイル方法"
  - "プロファイル ツール、同時実行メソッド"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プロファイリング ツールのリソース競合データ値について
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リソース競合プロファイルではアプリケーションの詳細な呼び出し履歴情報、競合するスレッドによる共有リソースへのアクセスで待機収集します。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 リソース競合レポートには、発生した競合の合計数と、リソースに対する合計待機時間 \(待機が発生したモジュール、関数、ソース コード行、命令についての合計待機時間\) が表示されます。  
  
-   包括値には、関数の待機の原因となったリソース競合の合計数と、関数の合計待機時間が表示されます。この関数から呼び出された子関数内で発生した競合についても、包括値に含まれます。  
  
-   排他値には、関数の待機の原因となった競合 \(関数本体内のコードによる競合\) の数だけが表示されます。  子関数から呼び出された競合は、排他値には含まれません。  この関数の排他時間についても、関数本体のステートメントが原因で発生した待機時間だけが含まれます。  
  
 リソース競合レポート ビューには、各競合イベントを示すタイムライン グラフが時系列に表示され、特定のイベントの作成元となった呼び出し履歴が表示されます。  詳細については、次のトピックを参照してください。  
  
-   [スレッドの詳細ビュー](../profiling/thread-details-view-contention-data.md)  
  
-   [リソースの詳細ビュー](../profiling/resource-details-view-contention-data.md)  
  
 同時プロファイリングのもう 1 つのモードの詳細については、「[同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)」を参照してください。