---
title: "データヒントのコード エディターでのデータ値の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 178bd1768474eaaaf760e2ef4feecfe0e1519bee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>コード エディターでデータヒントのデータ値の表示
DataTips は、デバッグ中にプログラムの変数に関する情報を確認するときに便利です。 データヒントは、中断モードのときにのみ機能します。また、実行の現在のスコープ内にある変数に対してだけ使用できます。
  
### <a name="to-display-a-datatip"></a>データヒントを表示するには  
  
1. ブレークポイントを設定し、デバッグを開始 (キーを押して**f5 キーを押して**)。

2. デバッガーで一時停止して、場所は、現在のスコープ内の変数にマウス ポインターを置きます。
  
     DataTip が表示されます。
  
3.  マウス ポインターを離すとデータヒントが表示されなくなります。 データヒントをピン留め、開いたままになるようにをクリックして、**ソースにピン留めする**アイコン、または変数を右クリックし、をクリックして**ソースにピン留めする**です。

    ![データのヒントをピン留め](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > データヒントは、プログラムの実行が中断され、カーソルがホバーしていないコンテキストで常に評価されます。 現在のコンテキスト内の変数と同じ名前の別の関数内の変数にポインターを合わせると、その別の関数内の変数の値が、現在のコンテキストの変数の値として表示されます。
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>データヒントの固定を解除してフローティングするには  
  
-   固定されたデータヒントでをクリックして、**ソースからのピン解除**アイコン。  
  
     ピン アイコンの表示が固定が解除された状態に変わり、 開いているすべてのウィンドウの上でデータヒントをフローティングできるようになります。 フローティング状態のデータヒントは、デバッグ セッションを終了すると閉じます。  
  
### <a name="to-repin-a-floating-datatip"></a>フローティング状態のデータヒントを再度固定するには  
  
-   データヒントで、ピン アイコンをクリックします。  
  
     ピン アイコンの表示が固定された状態に変わります。 データヒントがソース ウィンドウ外にある場合は、ピン アイコンが無効になり、データヒントを固定することはできません。  
  
### <a name="to-close-a-datatip"></a>データヒントを閉じるには  
  
-   データヒントに合わせ、マウス ポインターを置き、をクリックして、**閉じる**アイコン。  
  
### <a name="to-close-all-datatips"></a>すべてのデータヒントを閉じるには  
  
-   **デバッグ** メニューのをクリックして**すべてのデータヒントをクリア**です。  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>特定のファイルのすべてのデータヒントを閉じるには  
  
-   **デバッグ** メニューのをクリックして**クリアすべてのデータヒントにピン留め***ファイル*です。  
  
## <a name="expand-and-edit-information"></a>展開し、情報の編集  
 データヒントを使用すると、配列、構造体、またはオブジェクトを展開して、メンバーを表示できます。 DataTip の変数値を編集することもできます。  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>変数を展開して要素を表示するには  
  
-   データヒントで、経由でマウス ポインターを置き、  **+** 変数名の前に来る記号。  
  
    変数が展開され、ツリー形式で要素が表示されます。

    ![データ ヒントを表示する](../debugger/media/dbg-tour-data-tips.gif "データ ヒントを表示します。")
  
    変数を展開すると、キーボードの方向キーを使用して、上下に移動できます。 また、マウスも使用できます。  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>データヒントを使用して変数値を編集するには  
  
1.  データヒントで、値をクリックします。 読み取り専用の値では無効です。  
  
2.  新しい値を入力し、Enter キーを押します。  
  
## <a name="making-a-datatip-transparent"></a>DataTip を透過的にする  
 データヒントの背後にあるコードを確認する場合は、一時的にデータヒントを透過的に設定できます。 固定されているか、またはフローティング状態になっているデータヒントには適用されません。  
  
#### <a name="to-make-a-datatip-transparent"></a>DataTip を透過的にするには  
  
-   データヒントで、Ctrl キーを押します。  
  
     Ctrl キーを押している間、データヒントは透過的になります。  
  
## <a name="visualize-complex-data-types"></a>複合データ型を視覚化します。  
 データヒントで、1 つまたは複数の変数名の横にある虫眼鏡のアイコンが表示された場合は[ビジュアライザー](../debugger/create-custom-visualizers-of-data.md)など、[文字列ビジュアライザー](../debugger/string-visualizer-dialog-box.md)、そのデータ型の変数があります。 ビジュアライザーを使用すると、よりわかりやすい形式 (通常はグラフィック形式) で情報が表示されます。
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>ビジュアライザーを使用して変数の内容を表示するには  
  
-   虫眼鏡アイコンをクリックして![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")をデータ型の既定のビジュアライザーを選択します。  
  
     - または -  
  
     ビジュアライザーの横にあるポップアップ矢印をクリックし、データ型の適切なビジュアライザーを一覧から選択します。  
  
     ビジュアライザーに情報が表示されます。  
  
## <a name="add-information-to-a-watch-window"></a>[ウォッチ] ウィンドウに情報を追加します。  
 リスト ビュー内の変数のウォッチを継続する場合は、変数を追加することができます、**ウォッチ**データヒントからウィンドウです。  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>ウォッチ ウィンドウに変数を追加するには  
  
-   データヒントを右クリックし、をクリックして**ウォッチ式の追加**です。  
  
     変数を追加、**ウォッチ**ウィンドウです。 複数をサポートするエディションを使用している場合**ウォッチ**windows、変数に追加されて**ウォッチ 1 です。**  
  
## <a name="import-and-export-datatips"></a>インポートおよびデータヒントのエクスポート  
 データヒントは XML ファイルにエクスポートして、他のユーザーと共有したり、テキスト エディターで編集したりすることができます。  
  
#### <a name="to-export-datatips"></a>データヒントをエクスポートするには  
  
1.  デバッグ メニューをクリックして**データヒントのエクスポート**です。  
  
     **データヒントのエクスポート**  ダイアログ ボックスが表示されます。  
  
2.  XML ファイルを保存するファイルの名前を入力する場所に移動するファイルの標準的な手法を使用して、**ファイル名**ボックスし、をクリックして**OK**です。  
  
#### <a name="to-import-datatips"></a>データヒントをインポートするには  
  
1.  デバッグ メニューをクリックして**データヒントのインポート**です。  
  
     **データヒントのインポート**  ダイアログ ボックスが表示されます。  
  
2.  開き、をクリックする XML ファイルを検索 ダイアログ ボックスを使用して**OK**です。  
  
## <a name="see-also"></a>参照  
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [ウォッチと [クイック ウォッチ] ウィンドウ](../debugger/watch-and-quickwatch-windows.md)   
 [カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)   