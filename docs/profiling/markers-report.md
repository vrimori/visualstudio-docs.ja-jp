---
title: "マーカー レポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# マーカー レポート
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マーカーのレポート表示したタイム フレーム マーカー。画面または縮小または非 lane、マーカーが表示されるようにするか、無効にされることがあります。  レポートには、各プロパティについての情報が格納されます。T:  
  
-   これが開始時のトレースの開始に関連する時間。  
  
-   この長さ。  長さは、期間を表すためフラグとメッセージにはゼロです。  
  
-   これを生成したスレッドの ID。  
  
-   データを生成する ETW \(Event Tracing for Windows\) プロバイダーごとに追跡するイベント。  
  
-   これが書き込まれたマーカーのシリーズ。  
  
-   イベントのカテゴリ、に属しています。  
  
-   その重要性レベル。  
  
-   その型 \(範囲、フラグまたはメッセージ\)。  
  
-   表す内容の総合的な説明  
  
 マーカーを保存するに **\[エクスポート\]** ボタンを報告するように CSV ファイルをクリックします。  他のアプリケーションまたはツールを使って、CSV ファイルにデータを使用できます。  
  
> [!NOTE]
>  マーカーのレポートは 1,000 のマーカーを表示できます。  すべてのマーカーを参照するには、CSV ファイルに詳報をエクスポートします。