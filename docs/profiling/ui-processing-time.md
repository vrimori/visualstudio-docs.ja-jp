---
title: "UI 処理時間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "同時実行ビジュアライザー, UI 処理時間"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# UI 処理時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

タイムライン内のこれらのセグメントは、UI 処理として分類されるブロック時間と関連付けられています。  これは、1 つのスレッドが、Windows メッセージをポンプしているか、他のユーザー インターフェイス \(UI\) 作業を実行していることを意味します。  この時間の間、同時実行ビジュアライザーが UI 処理としてカウントしている API で、1 つのスレッドがブロックされています。  `GetMessage()` や `MsgWaitForMultipleObjects()` などの API がこのグループになります。  
  
 ブロックの原因となる定義済みの API を識別できない場合は、呼び出し履歴とプロファイル レポートを確認して、遅延の原因を判断します。  
  
 UI 処理カテゴリは、GUI アプリケーションの応答性を理解するのに重要であり、UI の応答性に依存するアプリケーションではこのカテゴリが推奨されます。  たとえば、アプリケーション内の UI スレッドが UI 処理で 100% の時間を達成した場合、非常に応答性が高いと思われます。  ただし、UI スレッドが他のカテゴリで長時間を費やしている場合は、根本的な原因を見つけて、そのスレッドでの UI 以外のカテゴリを削減するオプションを検討してください。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)