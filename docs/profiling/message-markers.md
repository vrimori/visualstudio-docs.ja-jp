---
title: "メッセージ マーカー | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 0fa95a9a7ff262f03608d5b076a45220d2b56fec
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---
# <a name="message-markers"></a>メッセージ マーカー
メッセージ マーカーは、ログ出力を表します。 メッセージは、特定のスレッドによって特定の時間に発行される文字列です。 メッセージは、その他のツールで使用するためにテキスト ファイルにエクスポートできます。 メッセージ文字列を確認するには、同時実行ビジュアライザーで、メッセージにポインターを置くことができます。 そして、[マーカー レポート](../profiling/markers-report.md)で、すべてのメッセージ マーカーを確認できます。  次の図は、メッセージ マーカーを示しています。  
  
## <a name="message-aggregation-markers"></a>メッセージの集約マーカー  
 同時実行ビジュアライザーで、複数のメッセージが相互に近接しすぎて、個別に描画できないことがあります。 そのような場合には、基になるメッセージを表す*メッセージ集約マーカー*が表示されます。 それらのアイコンのいずれかにポインターを置くと、表現されている、基になるメッセージの数がツールヒントに表示されます。 メッセージを表示するには、ズームインします。  限界までズームインしてもなお集約マーカーが表示される場合には、基になるメッセージを[マーカー レポート](../profiling/markers-report.md)で確認できます。  
  
## <a name="see-also"></a>関連項目  
 [同時実行ビジュアライザー マーカー](../profiling/concurrency-visualizer-markers.md)   
 [同時実行ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)
