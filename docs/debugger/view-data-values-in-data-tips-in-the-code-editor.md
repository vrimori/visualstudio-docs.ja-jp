---
title: データヒントで、コード エディターでのデータ値の表示 |Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afb318c8aa327345b3cd76ee16b718db1e0386aa
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826756"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>データヒントで、コード エディターで値のデータ表示
DataTips は、デバッグ中にプログラムの変数に関する情報を確認するときに便利です。 データヒントは、中断モードのときにのみ機能します。また、実行の現在のスコープ内にある変数に対してだけ使用できます。 コードをデバッグしようとした初めての場合は、読み取りをする可能性があります[優れたC#Visual Studio を使用してコード](../debugger/write-better-code-with-visual-studio.md)と[超初心者向けのデバッグ](../debugger/debugging-absolute-beginners.md)にこの記事に進む前にします。
  
### <a name="to-display-a-datatip"></a>データヒントを表示するには  
  
1. ブレークポイントを設定し、デバッグを開始 (キーを押して**F5**)。

2. デバッガーで一時停止されている現在のスコープ内の変数にマウス ポインターを置きます。
  
     DataTip が表示されます。
  
3.  マウス ポインターを離すとデータヒントが表示されなくなります。 未処理のままにするために、データヒントをピン留めする をクリックして、**ソースにピン留めする**アイコン、または変数を右クリックし、クリックして**ソースにピン留めする**します。

    ![データのヒントをピン留め](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > データヒントは、プログラムの実行が中断され、カーソルがホバーしていないコンテキストで常に評価されます。 現在のコンテキスト内の変数と同じ名前の別の関数内の変数にポインターを合わせると、その別の関数内の変数の値が、現在のコンテキストの変数の値として表示されます。
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>データヒントの固定を解除してフローティングするには  
  
-   固定されたデータヒント をクリックして、**ソースをピン解除**アイコン。  
  
     ピン アイコンの表示が固定が解除された状態に変わり、 開いているすべてのウィンドウの上でデータヒントをフローティングできるようになります。 フローティング状態のデータヒントは、デバッグ セッションを終了すると閉じます。  
  
### <a name="to-repin-a-floating-datatip"></a>フローティング状態のデータヒントを再度固定するには  
  
-   データヒントで、ピン アイコンをクリックします。  
  
     ピン アイコンの表示が固定された状態に変わります。 データヒントがソース ウィンドウ外にある場合は、ピン アイコンが無効になり、データヒントを固定することはできません。  
  
### <a name="to-close-a-datatip"></a>データヒントを閉じるには  
  
-   データヒントに合わせ、マウス ポインターを置きをクリックして、**閉じる**アイコン。  
  
### <a name="to-close-all-datatips"></a>すべてのデータヒントを閉じるには  
  
-   **デバッグ** メニューのをクリックして**すべてのデータヒントをクリア**します。  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>特定のファイルのすべてのデータヒントを閉じるには  
  
-   **デバッグ** メニューのをクリックして**クリアすべてデータヒントにピン留め***ファイル*します。  
  
## <a name="expand-and-edit-information"></a>展開し、情報の編集  
 データヒントを使用すると、配列、構造体、またはオブジェクトを展開して、メンバーを表示できます。 DataTip の変数値を編集することもできます。  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>変数を展開して要素を表示するには  
  
-   データヒントで、マウス ポインターを置く経由で、 **+** 変数名の前にサインオンします。  
  
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
 データヒント、1 つまたは複数の変数名の横にある虫眼鏡のアイコンが表示された場合[ビジュアライザー](../debugger/create-custom-visualizers-of-data.md)など、[文字列のビジュアライザーを](../debugger/string-visualizer-dialog-box.md)、そのデータ型の変数を利用します。 ビジュアライザーを使用すると、よりわかりやすい形式 (通常はグラフィック形式) で情報が表示されます。
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>ビジュアライザーを使用して変数の内容を表示するには  
  
-   虫眼鏡アイコンをクリックします。 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")データ型の既定のビジュアライザーを選択します。  
  
     - または -  
  
     ビジュアライザーの横にあるポップアップ矢印をクリックし、データ型の適切なビジュアライザーを一覧から選択します。  
  
     ビジュアライザーに情報が表示されます。  
  
## <a name="add-information-to-a-watch-window"></a>ウォッチ ウィンドウに情報を追加します。  
 リスト ビュー内の変数のウォッチを継続する場合は、変数を追加することができます、**ウォッチ**データヒントからウィンドウ。  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>ウォッチ ウィンドウに変数を追加するには  
  
-   データヒントを右クリックし、をクリックし、**ウォッチ式の追加**します。  
  
     変数を追加、**ウォッチ**ウィンドウ。 複数をサポートするエディションを使用している場合**ウォッチ**windows で、変数に追加されて**ウォッチ 1。**  
  
## <a name="import-and-export-datatips"></a>インポートして、データヒントのエクスポート  
 データヒントは XML ファイルにエクスポートして、他のユーザーと共有したり、テキスト エディターで編集したりすることができます。  
  
#### <a name="to-export-datatips"></a>データヒントをエクスポートするには  
  
1.  デバッグ メニューで、次のようにクリックします。**データヒントのエクスポート**します。  
  
     **データヒントのエクスポート**  ダイアログ ボックスが表示されます。  
  
2.  ファイルの名前を入力、XML ファイルを保存場所に移動するファイルの標準的な手法を使用して、**ファイル名**ボックスをクリックして**OK**します。  
  
#### <a name="to-import-datatips"></a>データヒントをインポートするには  
  
1.  デバッグ メニューで、次のようにクリックします。**データヒントのインポート**します。  
  
     **データヒントのインポート**  ダイアログ ボックスが表示されます。  
  
2.  開き、をクリックする XML ファイルを検索 ダイアログ ボックスを使用して**OK**します。  
  
## <a name="see-also"></a>関連項目  
 [何をデバッグするとしますか。](../debugger/what-is-debugging.md)  
 [優れたC#Visual Studio を使用するコード](../debugger/write-better-code-with-visual-studio.md)  
 [最初に、デバッグについて](../debugger/debugger-feature-tour.md)[デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [ウォッチ ウィンドウと [クイック ウォッチ] の Windows](../debugger/watch-and-quickwatch-windows.md)   
 [カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)   