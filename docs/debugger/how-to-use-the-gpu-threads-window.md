---
title: "デバッガーで GPU スレッドの表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b4782a1650034424d2616e47f46e07cec4d01ae5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-gpu-threads-window"></a>方法: GPU スレッド ウィンドウを使用する
GPU スレッド ウィンドウでは、デバッグ中のアプリケーション内の GPU 上で実行されているスレッドを調べて操作できます。 GPU 上で実行されるアプリケーションの詳細については、次を参照してください。 [C++ AMP の概要](/cpp/parallel/amp/cpp-amp-overview)です。  
  
 GPU スレッド ウィンドウには、すべての列で同じ値を持つ一連の GPU スレッドを各行が表すテーブルが表示されます。 列内の項目を並べ替え、順序変更、削除、およびグループ化することができます。 GPU スレッド ウィンドウから、スレッドのフラグ設定、フラグ解除、凍結 (中断)、および凍結解除 (再開) を実行できます。 GPU スレッド ウィンドウには次の列が表示されます。  
  
-   フラグ列。特に注意する必要のあるスレッドをマークできます。  
  
-   現在のスレッドの列、黄色の矢印が、現在のスレッドを示します。  
  
-   **スレッド数**列で、同じ場所にあるスレッドの数を表示します。  
  
-   **行**列で、スレッドの各グループが配置されているコードの行が表示されます。  
  
-   **アドレス**列で、スレッドの各グループがある命令アドレスが表示されます。 既定では、この列は非表示になっています。  
  
-   **場所**列で、ソース コード内の位置です。  
  
-   **ステータス**列で、スレッドがアクティブ、ブロック、未開始、または完了するかどうかを示します。  
  
-   **タイル**列で、行のスレッドのタイル インデックスを示します。  
  
 テーブルのヘッダーは、表示されているタイルとスレッドを示します。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>GPU スレッド ウィンドウを表示するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]**をクリックします。  
  
2.  **プロパティ ページ**、プロジェクトのウィンドウで**構成プロパティ**、選択**デバッグ**です。  
  
3.  **起動するデバッガー**一覧で、**ローカル Windows デバッガー**です。 **デバッガーの種類**一覧で、 **GPU のみ**です。 GPU 上で実行されるコードのブレークポイントで中断するには、このデバッガーを選択する必要があります。  
  
4.  **[OK]** を選択します。  
  
5.  GPU コードにブレークポイントを設定します。  
  
6.  メニュー バーで、**[デバッグ]**、**[デバッグ開始]** の順に選択します。 アプリケーションがブレークポイントに到達するを待機します。  
  
7.  メニュー バーのいずれかを選択して**デバッグ**、 **Windows**、 **GPU スレッド**です。  
  
### <a name="to-switch-to-a-different-thread"></a>別のスレッドに切り替えるには  
  
-   列をダブルクリックします。 (キーボード: 行を選択し、Enter キーを押します。)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>特定のタイルとスレッドを表示するには  
  
1.  選択、 **[スレッド スイッチャーの**GPU スレッド] ウィンドウでボタンをクリックします。  
  
2.  テキスト ボックスにタイルとスレッドの値を入力します。  
  
3.  矢印が表示されているボタンをクリックします。  
  
### <a name="to-display-or-hide-a-column"></a>列の表示と非表示を切り替えるには  
  
-   GPU スレッド ウィンドウのショートカット メニューを開き、選択**列**、表示または非表示にする列を選択します。  
  
### <a name="to-sort-by-a-column"></a>列で並べ替えるには  
  
-   列見出しを選択します。  
  
### <a name="to-group-threads"></a>スレッドをグループ化するには  
  
-   GPU スレッド ウィンドウのショートカット メニューを開き、選択**Group By**、表示される列名のいずれかを選択します。 選択**None**スレッドのグループ化を解除します。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>スレッドの行を凍結または凍結解除するには  
  
-   行のショートカット メニューを開き**凍結**または**凍結解除**です。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>スレッドの行をフラグ設定またはフラグ解除するには  
  
-   スレッドのフラグ列を選択し、スレッドのショートカット メニューを開きまたは選択**フラグ**または**フラグ解除**です。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   GPU スレッド ウィンドウでフラグ ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法: 並列ウォッチ ウィンドウの使用](../debugger/how-to-use-the-parallel-watch-window.md)   
 [チュートリアル: C++ AMP アプリケーションのデバッグ](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)