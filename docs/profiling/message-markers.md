---
title: "メッセージ マーカー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.message"
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# メッセージ マーカー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

メッセージのマーカーは、ログ出力を表します。  メッセージは、特定のスレッドによって特定の時間に発行された文字列です。  そのほかのツールで使用するテキスト ファイルにメッセージをエクスポートできます。  メッセージ文字列を表示するには、同時実行ビジュアライザーのメッセージ ポインターを置くことができます。  [マーカー レポート](../profiling/markers-report.md)とすべてのメッセージのマーカーを表示できます。次の図は、メッセージのマーカーを示しています。  
  
## メッセージの集計のマーカー  
 複数のメッセージは、描画できません。したがって、同時実行ビジュアライザーが互いに近い行われます。  この場合、基になるメッセージを表す *メッセージの集計のマーカーが* 表示されます。  これらのアイコンの 1 つがにポインターを置くと、ツール ヒントが表示される基になるメッセージの数。  メッセージを表示するには、拡大します。ズーム インしても、集計のマーカーを取得し、[マーカー レポート](../profiling/markers-report.md)の基になるメッセージを表示できます。  
  
## 参照  
 [同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)   
 [同時実行ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)