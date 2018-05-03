---
title: Visual Studio でのロード テスト用のグラフ作成カウンターのプロット オプション
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8e17d0f9e25616f70e1d5f74cd0ed4916efc7b8b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>方法: グラフ作成カウンターのプロット オプションを指定する

**[プロット オプション]** ダイアログ ボックスを使用すると、グラフにプロットされるカウンターの色と線スタイルを変更できます。 サンプル データに基づいて、特定の値で範囲を固定したり、その範囲が自動的に調整されるように設定したりすることもできます。

![[プロット オプション] ダイアログ ボックス](../test/media/ltest_plotoptions.png "LTest_PlotOptions")

## <a name="to-specify-plotting-options-for-graphs"></a>グラフのプロット オプションを指定するには

1.  ロード テスト アナライザーで、ロード テスト ツール バーの **[グラフ]** を選択します。

     ロード テストの結果がグラフ ビューに表示されます。

2.  凡例またはグラフのいずれかで、プロット オプションを変更するパフォーマンス カウンターの行または現在のプロット線を右クリックし、**[プロット オプション]** を選択します。

     **[プロット オプション]** ダイアログ ボックスが表示されます。

3.  **[色]** ドロップダウン リストを使用して、パフォーマンス カウンターのプロットに使用する色を選択します。

4.  **[スタイル]** ドロップダウン リストを使用して、パフォーマンス カウンターのプロットに使用するスタイルを選択します。

5.  次のいずれかの操作を行います。

     **[自動的に範囲を調整]** (既定) を選択します。

     \- または

     **[自動的に範囲を調整]** を解除し、**[範囲]** ドロップダウン リストを使用して、パフォーマンス カウンターのプロットに使用する範囲を指定します。

6.  **[OK]** をクリックします。

     オプションを変更したパフォーマンス カウンターが、変更を指定したグラフに表示されます。

## <a name="see-also"></a>関連項目

- [グラフ ビューでのロード テスト結果の分析](../test/analyze-load-test-results-in-the-graphs-view.md)
- [方法: カスタム グラフを作成する](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [グラフ ビューでのロード テスト結果の分析](../test/analyze-load-test-results-in-the-graphs-view.md)