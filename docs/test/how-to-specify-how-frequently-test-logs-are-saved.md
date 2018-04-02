---
title: Visual Studio でのロード テストのログの保存 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0178be52299183a072532d62f323a4612a93f531
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>方法: ロード テスト エディターを使用してテスト ログの保存頻度を指定する

**新しいロード テスト ウィザード**でロード テストを作成した後で、**ロード テスト エディター**を使用して、ロード テストのプロパティをテストのニーズおよび目標に合わせて変更できます。 詳細については、「[Walkthrough: Create and run a load test](../test/walkthrough-create-and-run-a-load-test.md)」(チュートリアル: ロード テストの作成および実行) を参照してください。

> [!NOTE]
> 実行設定の各プロパティとその説明の一覧については、「[Load Test Run Settings Properties](../test/load-test-run-settings-properties.md)」(ロード テストの実行設定のプロパティ) を参照してください。

ロード テスト エディターを使用して、[プロパティ] ウィンドウで **[完了したテストのログ頻度を保存]** プロパティを変更することにより、ロード テストでテスト ログを保存する頻度を指定できます。

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>ロード テストでテスト ログを保存する頻度を指定するには

1.  ロード テストを開きます。

     ロード テスト エディターが表示されます。 ロード テスト ツリーが表示されます。

2.  ロード テスト ツリーの **[実行設定]** フォルダーで、テスト ログを保存する頻度を指定する実行設定ノードを選択します。

3.  **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。

     [プロパティ] ウィンドウに、シナリオのカテゴリおよびプロパティが表示されます。

4.  **[完了したテストのログ頻度を保存]** プロパティのテキスト ボックスに、テスト ログが書き込まれる頻度を示す数値を入力します。 この数値は、入力したテストの数のうち 1 回がテスト ログに保存されることを示します。 たとえば、値 10 を入力すると、10 番目、20 番目、30 番目などのテストがテスト ログに書き込まれます。

    > [!NOTE]
    > **[完了したテストのログ頻度を保存]** プロパティを 0 に設定すると、テスト ログの保存は指定されません。

5.  プロパティを変更したら、**[ファイル]** メニューの **[保存]** を選択します。

     ロード テスト アナライザーのテーブル ビューを使用すると、ログに保存したデータを表示できます。 詳細については、[テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)
- [チュートリアル: ロード テストの作成と実行](../test/walkthrough-create-and-run-a-load-test.md)
- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)
- [方法: テスト ログにテストの失敗を記録するかどうかを指定する](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [方法: すべての詳細情報を収集するように構成して仮想ユーザー アクティビティ チャートを有効にする](../test/how-to-configure-load-tests-to-collect-full-details.md)