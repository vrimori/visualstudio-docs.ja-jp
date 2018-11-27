---
title: '方法: GPU スレッド ウィンドウを使用して、|Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8afd9cd09cf5977f58ee3a48b891f5291869b49c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799172"
---
# <a name="how-to-use-the-gpu-threads-window"></a>方法: GPU スレッド ウィンドウを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

GPU スレッド ウィンドウでは、デバッグ中のアプリケーション内の GPU 上で実行されているスレッドを調べて操作できます。 GPU 上で実行されるアプリケーションの詳細については、次を参照してください。 [C++ AMP の概要](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc)します。  
  
 GPU スレッド ウィンドウには、すべての列で同じ値を持つ一連の GPU スレッドを各行が表すテーブルが表示されます。 列内の項目を並べ替え、順序変更、削除、およびグループ化することができます。 GPU スレッド ウィンドウから、スレッドのフラグ設定、フラグ解除、凍結 (中断)、および凍結解除 (再開) を実行できます。 GPU スレッド ウィンドウには次の列が表示されます。  
  
- フラグ列。特に注意する必要のあるスレッドをマークできます。  
  
- アクティブ スレッド列。黄色の矢印は、アクティブ スレッドであることを示します。 矢印は、実行がデバッガーに割り込んだスレッドを示します。  
  
- **Thread Count**列は、同じ場所にあるスレッドの数が表示されます。  
  
- **行**列は、スレッドの各グループが配置されるコードの行が表示されます。  
  
- **アドレス**列は、スレッドの各グループのある命令アドレスが表示されます。 既定では、この列は非表示になっています。  
  
- **場所**列は、ソース コード内の位置です。  
  
- **状態**列は、スレッドがアクティブ、ブロック、未開始、または完全なかどうかを示します。  
  
- **タイル**列は、行のスレッドのタイル インデックスを示しています。  
  
  テーブルのヘッダーは、表示されているタイルとスレッドを示します。  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>GPU スレッド ウィンドウを表示するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。  
  
2.  **プロパティ ページ**、プロジェクトのウィンドウで**構成プロパティ**、選択**デバッグ**します。  
  
3.  **起動するデバッガー**一覧で、**ローカル Windows デバッガー**します。 **デバッガーの種類**一覧で、 **GPU のみ**します。 GPU 上で実行されるコードのブレークポイントで中断するには、このデバッガーを選択する必要があります。  
  
4.  **[OK]** を選択します。  
  
5.  GPU コードにブレークポイントを設定します。  
  
6.  メニュー バーで、**[デバッグ]**、**[デバッグ開始]** の順に選択します。 アプリケーションがブレークポイントに到達するを待機します。  
  
7.  メニュー バーで、1 つを選択**デバッグ**、 **Windows**、 **GPU スレッド**します。  
  
### <a name="to-change-to-a-different-active-thread"></a>別のアクティブなスレッドに変更するには  
  
-   列をダブルクリックします。 (キーボード: 行を選択し、Enter キーを押します。)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>特定のタイルとスレッドを表示するには  
  
1.  選択、 **[スレッド スイッチャー** GPU スレッド] ウィンドウでボタンをクリックします。  
  
2.  テキスト ボックスにタイルとスレッドの値を入力します。  
  
3.  矢印が表示されているボタンをクリックします。  
  
### <a name="to-display-or-hide-a-column"></a>列の表示と非表示を切り替えるには  
  
-   GPU スレッド ウィンドウのショートカット メニューを開き、選択**列**、し、表示または非表示にする列を選択します。  
  
### <a name="to-sort-by-a-column"></a>列で並べ替えるには  
  
-   列見出しを選択します。  
  
### <a name="to-group-threads"></a>スレッドをグループ化するには  
  
-   GPU スレッド ウィンドウのショートカット メニューを開き、選択**Group By**、表示される列名のいずれかを選択します。 選択**None**スレッドのグループ化を解除します。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>スレッドの行を凍結または凍結解除するには  
  
-   行のショートカット メニューを開いて**固定**または**凍結解除**します。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>スレッドの行をフラグ設定またはフラグ解除するには  
  
-   スレッドのフラグ列を選択またはスレッドのショートカット メニューを開くし、選択**フラグ**または**フラグ解除**します。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   GPU スレッド ウィンドウでフラグ ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法: 並列ウォッチ ウィンドウの使用](../debugger/how-to-use-the-parallel-watch-window.md)   
 [チュートリアル: C++ AMP アプリケーションのデバッグ](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



