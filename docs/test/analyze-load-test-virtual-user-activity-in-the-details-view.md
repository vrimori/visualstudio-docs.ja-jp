---
title: Visual Studio でのロード テストの仮想ユーザー アクティビティの分析 | Microsoft Docs
ms.date: 10/03/2016
ms.topic: article
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 149c56f5100c8a9e92108970d29d502a359181b0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>ロード テスト アナライザーの詳細ビューでのロード テストの仮想ユーザー アクティビティの分析

**仮想ユーザー アクティビティ チャート**

 ![仮想ユーザー アクティビティ チャート](../test/media/virtual_actchart.png "Virtual_ActChart")

 詳細ビューには、ロード テスト中に各仮想ユーザーが実行していた操作を視覚的に分析するための仮想ユーザー アクティビティ チャートが表示されます。 仮想ユーザー アクティビティ チャートで、ユーザー アクティビティのパターンとロード パターンを表示して、失敗したテストや時間のかかったテストを関連付け、他の仮想ユーザー アクティビティによる要求を確認できます。 仮想ユーザー アクティビティ チャートは、CPU 使用率のスパイク、1 秒あたりの要求数のドロップ、および、スパイクとドロップの間に実行されていたテストまたはページを調べるのに役立ちます。

> [!NOTE]
> 仮想ユーザー アクティビティ詳細チャートを使用するロード テストを実行する前に、ロード パフォーマンス テスト エディターを使用して、**[タイミングの詳細ストレージ]** プロパティが **[AllIndividualDetails]** に設定されていることを確認する必要があります。 詳細については、[すべての詳細情報を収集するように構成して仮想ユーザー アクティビティ チャートを有効にする方法](../test/how-to-configure-load-tests-to-collect-full-details.md)に関するページを参照してください。

 **[詳細の凡例] パネル**

 ![[詳細の凡例] パネル](../test/media/ltest_detailslegend.png "LTest_DetailsLegend")

 [詳細の凡例] パネルは、仮想ユーザー アクティビティ チャートに表示されます。 [詳細の凡例] パネルを使用すると、数種類の基準に基づいてテスト、ページ、およびトランザクションを除外できます。 たとえば、ビューから特定のテストを削除したり、成功したすべてのテストを削除したりできます。特定のエラーで失敗したテストを削除することもできます。 ログがないテストをすべて削除することもできます。

 失敗したテストを強調表示すると、失敗したテストがすべて赤で表示されます。 テスト ログのあるテストを強調表示することもできます。 ログのあるテストは緑で表示されます。

 **[フィルター結果] パネル**

 ![[フィルター結果] パネル](../test/media/ltest_filterresults.png "LTest_FilterResults")

 [フィルター結果] パネルは、仮想ユーザー アクティビティ チャートに表示されます。 [フィルター結果] パネルでは、次のように結果がフィルターされます。

-   **[ログのある結果のみを表示]** 関連付けられたテスト ログがあるテスト結果のみが表示されます。

-   **[成功した結果の表示]** 成功した結果が表示されます。

-   **[エラーのある結果の表示]** デバッグに役立つエラーのある結果が表示されます。

## <a name="tasks"></a>[タスク]

|[タスク]|関連するトピック|
|-----------|-----------------------|
|**仮想ユーザー アクティビティ チャートを使用するためのロード テストの構成:** 仮想ユーザー アクティビティ データを表示するロード テストを実行する前に、まずロード テストのプロパティ設定を構成する必要があります。|-   [方法: すべての詳細情報を収集するように構成して仮想ユーザー アクティビティ チャートを有効にする](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**ロード テストの実行:** ロード テストを作成し、仮想ユーザー アクティビティ データを収集するように構成したら、テストを実行して完了し、仮想ユーザー アクティビティ チャートを表示できるようにします。||
|**仮想ユーザー アクティビティ データを含むロード テスト結果の表示:** ロード テストの作成、構成、実行が完了したら、仮想ユーザー アクティビティ チャートを使用して仮想ユーザー アクティビティ データを表示できます。|-   [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [方法: ロード テスト中に仮想ユーザーが行っている操作を分析する](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**ロード テスト時のパフォーマンスの問題の特定:** 仮想ユーザー アクティビティ チャートを使用して、ロード テストにおけるパフォーマンスの問題を特定できます。|-   [チュートリアル: 仮想ユーザー アクティビティ チャートを使用した問題の特定](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)