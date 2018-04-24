---
title: Visual Studio で失敗したテストのロード テスト ログを保存する | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 17b8792a98473658ae6ac47cd418028ce2cfcf6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>方法: ロード テスト エディターを使用してテスト ログにテストの失敗を記録するかどうかを指定する

**新しいロード テスト ウィザード**でロード テストを作成した後で、**ロード テスト エディター**を使用して、ロード テストのプロパティをテストのニーズおよび目標に合わせて変更できます。 「[Walkthrough: Create and Run a Load Test that contains Unit Tests](../test/walkthrough-create-and-run-a-load-test.md)」(チュートリアル: ロード テストの作成と実行) を参照してください。 **[テストの失敗時にログを保存]** プロパティを変更することにより、ロード テストでテストが失敗した場合にログを保存するかどうかを指定できます。

> [!NOTE]
>  実行設定の各プロパティとその説明の一覧については、「[Load Test Run Settings Properties](../test/load-test-run-settings-properties.md)」(ロード テストの実行設定のプロパティ) を参照してください。

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>シナリオでテストが失敗した場合にテスト ログを保存するには

1.  ロード テストを開きます。

     ロード テスト エディターが表示されます。 ロード テスト ツリーが表示されます。

2.  ロード テスト ツリーの **[実行設定]** フォルダーで、テスト イテレーションの最大数を指定する実行設定ノードを選択します。

3.  **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。

     [プロパティ] ウィンドウに、実行設定のカテゴリおよびプロパティが表示されます。

4.  **[テストの失敗時にログを保存]** プロパティで、[True] または [False] を選択して、シナリオでテストが失敗した場合にテスト ログを保存するかどうかを指定します。

     プロパティを変更したら、**[ファイル]** メニューの **[保存]** を選択します。

     ロード テスト アナライザーのテーブル ビューを使用すると、ログに保存したデータを表示できます。 詳細については、[テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)
- [チュートリアル: ロード テストの作成と実行](../test/walkthrough-create-and-run-a-load-test.md)
- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)
- [方法: すべての詳細情報を収集するように構成して仮想ユーザー アクティビティ チャートを有効にする](../test/how-to-configure-load-tests-to-collect-full-details.md)
- [方法: テスト ログの保存頻度を指定する](../test/how-to-specify-how-frequently-test-logs-are-saved.md)