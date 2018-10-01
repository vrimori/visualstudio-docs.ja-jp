---
title: '方法: 並列ウォッチ ウィンドウを使用して、|Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88c4efe15e2afd3f4158b93cf8701109cd3902b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540262"
---
# <a name="how-to-use-the-parallel-watch-window"></a>方法: 並列ウォッチ ウィンドウを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[並列スレッドの変数のウォッチを設定](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-parallel-watch-window)します。  
  
[並列ウォッチ] ウィンドウには、複数のスレッドで 1 つの式が保持している値を同時に表示できます。 各行は、1 つのアプリケーションで実行中のスレッドを表しますが、スレッドは複数の行に表示される場合があります。 具体的には、各行は関数シグネチャが現在のスタック フレーム上の関数に一致する関数呼び出しを表します。 列内の項目の並べ替え、順序変更、削除、およびグループ化を行うことができます。 スレッドのフラグ設定、フラグ解除、凍結 (中断)、および凍結解除 (再開) を実行できます。 次の列が表示されます、**並列ウォッチ**ウィンドウ。  
  
-   フラグ列。特に注意する必要のあるスレッドをマークできます。  
  
-   フレーム列。矢印は、選択したフレームを示します。  
  
-   構成可能な列。コンピューター、プロセス、タイル、タスク、スレッドを表示できます。  
  
    > [!TIP]
    >  開く必要があります、**並列タスク**でタスク情報を表示するウィンドウ、**並列ウォッチ**ウィンドウ。  
  
-   **\<ウォッチ式の追加 >** 列、ウォッチする式を入力することができます。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>[並列ウォッチ] ウィンドウを表示するには  
  
1.  コード内にブレークポイントを設定します。  
  
2.  メニュー バーで、**[デバッグ]**、**[デバッグ開始]** の順に選択します。 アプリケーションがブレークポイントに到達するを待機します。  
  
3.  メニュー バーで、**デバッグ**、 **Windows**、**並列ウォッチ**、ウォッチ ウィンドウを選択します。 最大で 4 つのウィンドウを開くことができます。  
  
### <a name="to-add-a-watch-expression"></a>ウォッチ式を追加するには  
  
-   選択**\<ウォッチ式の追加 >** し、ウォッチ式を指定します。  
  
### <a name="to-flag-or-unflag-a-thread"></a>スレッドのフラグを設定または設定解除するには  
  
-   フラグ列、行の選択、スレッドのショートカット メニューを開きまたは選択**フラグ**または**フラグ解除**します。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   左上隅にあるのみのフラグが設定を表示するボタンを選択、**並列ウォッチ**ウィンドウ。  
  
### <a name="to-switch-frames"></a>フレームを切り替えるには  
  
-   フレーム列をダブルクリックします  (キーボード: 行を選択し、Enter キーを押します)。  
  
### <a name="to-sort-a-column"></a>列を並べ替えるには  
  
-   列見出しを選択します。  
  
### <a name="to-group-threads"></a>スレッドをグループ化するには  
  
-   並列ウォッチ ウィンドウのショートカット メニューを開き、選択**Group By**、適切なサブメニュー項目を選択します。  
  
### <a name="to-freeze-or-thaw-threads"></a>スレッドを凍結/凍結解除するには  
  
-   行のショートカット メニューを開いて**固定**または**凍結解除**します。  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>[並列ウォッチ] ウィンドウ内のデータをエクスポートするには  
  
-   選択、 **Excel で開く**ボタンをクリックし、 **Excel で開く**または**CSV にエクスポート**します。  
  
### <a name="to-filter-by-a-boolean-expression"></a>ブール式でフィルター処理するには  
  
-   ブール式を入力してください、**ブール式でフィルター**ボックス。 デバッガーは、スレッド コンテキストの式を評価します。 値が `true` である行だけが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法: GPU スレッド ウィンドウを使用](../debugger/how-to-use-the-gpu-threads-window.md)   
 [チュートリアル: C++ AMP アプリケーションのデバッグ](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



