---
title: 並列スレッドの変数にウォッチを設定 |Microsoft Docs
ms.date: 04/25/2017
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86111c5ac40e4379e1130bdf143e736dec1494f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021469"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Visual Studio での並列スレッドの変数のウォッチ ポイントを設定 (C#、Visual Basic、C++)
[並列ウォッチ] ウィンドウには、複数のスレッドで 1 つの式が保持している値を同時に表示できます。 各行は、1 つのアプリケーションで実行中のスレッドを表しますが、スレッドは複数の行に表示される場合があります。 具体的には、各行は関数シグネチャが現在のスタック フレーム上の関数に一致する関数呼び出しを表します。 列内の項目の並べ替え、順序変更、削除、およびグループ化を行うことができます。 スレッドのフラグ設定、フラグ解除、凍結 (中断)、および凍結解除 (再開) を実行できます。 **[並列ウォッチ]** ウィンドウには次の列が表示されます。  
  
- フラグ列。特に注意する必要のあるスレッドをマークできます。  
  
- スレッドの現在の列の黄色の矢印が、現在のスレッドを示します (巻いた尾の付いた緑色の矢印は、現在ではないスレッドの現在のデバッガーのコンテキストであることを示します)。  
  
- 構成可能な列。コンピューター、プロセス、タイル、タスク、スレッドを表示できます。  
  
  > [!TIP]
  >  タスク情報を表示する、**並列ウォッチ**ウィンドウを開く必要があります最初、**タスク**ウィンドウ。  
  
- 空白*ウォッチ式の追加*列、ウォッチする式を入力することができます。  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>[並列ウォッチ] ウィンドウを表示するには  
  
1.  コード内にブレークポイントを設定します。  
  
2.  メニュー バーで、**[デバッグ]**、**[デバッグ開始]** の順に選択します。 アプリケーションがブレークポイントに到達するを待機します。  
  
3.  メニュー バーで、**[デバッグ]**、**[ウィンドウ]**、**[並列ウォッチ]** の順にクリックして、ウォッチ ウィンドウを選択します。 最大で 4 つのウィンドウを開くことができます。  
  
### <a name="to-add-a-watch-expression"></a>ウォッチ式を追加するには  
  
-   空白のいずれかを選択*ウォッチ式の追加*列し、ウォッチ式を入力します。  
  
### <a name="to-flag-or-unflag-a-thread"></a>スレッドのフラグを設定または設定解除するには  
  
-   行のフラグ列を選択します (最初の列) のスレッドのショートカット メニューを開き、または選択**フラグ**または**フラグ解除**します。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   選択、**表示のみにフラグが設定された**の左上隅のボタン、**並列ウォッチ**ウィンドウ。  
  
### <a name="to-switch-to-another-thread"></a>別のスレッドに切り替える  
  
-   現在のスレッドの列をダブルクリックします (2 番目の列)。 (キーボード:行を選択し、Enter キーを押します。)  
  
### <a name="to-sort-a-column"></a>列を並べ替えるには  
  
-   列見出しを選択します。  
  
### <a name="to-group-threads"></a>スレッドをグループ化するには  
  
-   [並列ウォッチ] ウィンドウのショートカット メニューを開いて **[グループ化]** をクリックし、適切なサブメニュー項目を選択します。  
  
### <a name="to-freeze-or-thaw-threads"></a>スレッドを凍結/凍結解除するには  
  
-   行のショートカット メニューを開き、**[凍結]** または **[凍結解除]** をクリックします。  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>[並列ウォッチ] ウィンドウ内のデータをエクスポートするには  
  
-   **[Excel で開く]** ボタンを選択して、**[Excel で開く]** または **[CSV にエクスポート]** を選択します。  
  
### <a name="to-filter-by-a-boolean-expression"></a>ブール式でフィルター処理するには  
  
-   **[ブール式でフィルター]** ボックスにブール式を入力します。 デバッガーは、スレッド コンテキストの式を評価します。 値が `true` である行だけが表示されます。  
  
## <a name="see-also"></a>関連項目
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法: [GPU スレッド] ウィンドウを使用する](../debugger/how-to-use-the-gpu-threads-window.md)   
 [チュートリアル: C++ AMP アプリケーションのデバッグ](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
