---
title: '方法 : インストルメンテーションで短い関数を除外または含める | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f77ae6260fa7401f8afa8030f551227baf50fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>方法 : インストルメンテーションで短い関数を除外または含める
既定では、プロファイリング ツールは*小規模関数*をインストルメンテーションから除外します。 小規模関数とは、関数の呼び出しを行わない短い関数のことです。 小規模関数を除外すると、インストルメンテーション オーバーヘッドが軽減するため、インストルメンテーションの速度が向上します。 また、小規模関数の除外によりパフォーマンス プロファイル データ ファイル (.vsp) のサイズが小さくなるため、分析に要する時間が短縮されます。 小規模関数が除外されると、その親関数の排他時間と包括時間に対して、小規模関数に費やされる時間が除外されます。 次に、インストルメンテーションで小規模関数を除外または含める手順について説明します。  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>インストルメンテーションで短い関数を除外または含めるには  
  
1.  **パフォーマンス エクスプローラー**で、**パフォーマンス セッション**を選択します。次に、右クリックして **[プロパティ]** を選択します。  
  
     **[プロパティ ページ]** ダイアログ ボックスが表示されます。  
  
2.  **[プロパティ ページ]** で、**[インストルメンテーション]** プロパティをクリックします。  
  
3.  インストルメンテーションから短い関数を除外するには、**[短い関数をインストルメンテーションから除外]** をオンにします。 これは、既定の設定です。  
  
     - または -  
  
     インストルメンテーションに短い関数を含めるには、**[短い関数をインストルメンテーションから除外]** をオフにします。  
  
4.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [データ コレクションの制御](../profiling/controlling-data-collection.md)   
 [パフォーマンス セッションのプロパティ](../profiling/performance-session-properties.md)