---
title: "スパン マーカー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.span"
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# スパン マーカー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

範囲のマーカーはアプリケーションの意味のある結果を表します。  たとえば、特定の作業項目が処理される時間の間隔を表すために範囲を使用できます。  この長さは対応するアプリケーション フェーズの長さを表します。  この図は、同時実行ビジュアライザーに範囲を持つ T:  
  
 ![同時実行ビジュアライザーのスパン マーカー](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
同時実行ビジュアライザーの範囲のマーカー  
  
## 範囲のカテゴリ  
 範囲のマーカーはカテゴリによって 5 種類の 1 色で表示されます。  色は、5 つ以上のカテゴリがある繰り返されます。  カテゴリは、整数になります。  この図には、5 とおりの色を示します:  
  
 ![異なるカテゴリの 5 つの範囲](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
最初の 5 個の範囲のカテゴリの色  
  
## 範囲の集計のマーカー  
 この範囲のマーカーは、描画できません。したがって、同時実行ビジュアライザーが互いに近い発生します。  この場合、基になる範囲を表す灰色の *範囲の集計のマーカーが* 表示されます。  これらのアイコンの 1 つがにポインターを置くと、ツール ヒントが表示される基の範囲の数。  範囲を表示するには、拡大します。  ズーム インしても、範囲の集計のマーカーを取得し、[マーカー レポート](../profiling/markers-report.md)の基になる範囲のマーカーを表示できます。  この図は、範囲の集計のマーカーを示します:  
  
 ![同時実行ビジュアライザーの集約スパン マーカー](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
範囲の集計のマーカー  
  
## 参照  
 [同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)   
 [同時実行ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)