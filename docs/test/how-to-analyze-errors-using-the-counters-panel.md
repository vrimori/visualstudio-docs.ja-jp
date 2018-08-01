---
title: Visual Studio でカウンター パネルを使用してロード テストのエラーを分析する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e7ccd21e5432003de7ec3b03bf94716802846bd4
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204337"
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>方法: カウンター パネルを使用してエラーを分析する

**[カウンター]** パネルは、ロード テストが実行中か、ロード テスト結果を分析しているとき、**ロード テスト アナライザー**にグラフ ビューおよびテーブル ビューで表示されます。 詳細については、「[グラフ ビューでのロード テスト結果の分析](../test/analyze-load-test-results-in-the-graphs-view.md)」、「[テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)」、「[方法 : ロード テストの結果にアクセスして分析する](../test/how-to-access-load-test-results-for-analysis.md)」 をご覧ください。

 **[カウンター]** パネルの **[エラー]** ノードには、ロード テスト中に検出されたすべてのエラーが含まれています。 **[エラー]** ノードには、さまざまなエラーに固有のサブカテゴリ エラー ノードが複数含まれています。 たとえば、**[例外]** や **[HTTP エラー]** などです。

 ![カウンター パネルのエラー ノード](../test/media/ltest_errornode.png)

## <a name="to-analyze-errors-in-the-counters-panel"></a>[カウンター] パネルでエラーを分析するには

1.  ロード テストの完了後またはテスト結果の読み込み後、ロード テスト アナライザーのツール バーの **[グラフ]** または **[テーブル]** を選択します。

     **[カウンター]** パネルがグラフ ビューまたはテーブル ビューで表示されます。

2.  **[カウンター]** パネルが表示されない場合、ツール バーの **[カウンター パネルの表示]** を選択します。

3.  **[エラー]** を展開し、分析するエラー カテゴリまたはエラー サブカテゴリを選択します。

4.  エラーを右クリックし、次のオプションのいずれかを選択します。

    -   **[グラフにカウンターを表示]**: グラフ ビューで、エラーが追加され、選択したグラフで強調表示されます。 詳細については、「[方法: グラフにカウンターを追加および削除する](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)」を参照してください。

    -   **[凡例にカウンターを表示]**: 凡例で、エラーが追加および選択されます。 詳細については、「[グラフ ビューの凡例を使用したロード テストの分析](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)」を参照してください。

    -   **[グラフの追加]**:

    1.  **[グラフ名の入力]** ダイアログ ボックスが表示されます。

    2.  **[グラフ名]** ボックスに新しいグラフの名前を入力し、**[OK]** を選択します。

    3.  (省略可能) エラーを再度右クリックし、**[グラフにカウンターを表示]** をクリックします。

         詳細については、「[方法: カスタム グラフを作成する](../test/how-to-create-custom-graphs-in-load-test-results.md)」を参照してください。

5.  (省略可能) 完了したロード テスト結果のエラーを分析する場合、グラフでのズーム機能の使用を検討してください。 詳細については、「[方法: グラフの領域にズーム インする](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)」を参照してください。

    > [!TIP]
    > ロード テストの実行中にエラーが検出された場合、エラーというリンクが**ロード テスト アナライザー**のステータス バーに表示され、検出された数が示されます。 このリンクを選択すると、テーブル ビューの**エラー** テーブルにすべてのエラーが表示されます。

## <a name="see-also"></a>関連項目

- [グラフ ビューおよびテーブル ビューでのカウンター パネルの使用](../test/counters-panel-in-load-test-analyzer.md)
- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)