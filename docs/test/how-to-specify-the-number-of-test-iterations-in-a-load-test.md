---
title: Visual Studio でテストの実行設定にテスト イテレーションの数を指定する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1c9122ec3f6eaed156c48f6fd31b4cbbed32292b
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179649"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>方法: テスト イテレーションの数をテストの実行設定に指定する

**新しいロード テスト** ウィザードでロード テストを作成した後で、**ロード テスト エディター**を使用して、テストのニーズや目標に合わせてシナリオのプロパティを変更できます。 詳細については、「[Walkthrough: Create and run a load test](../test/walkthrough-create-and-run-a-load-test.md)」(チュートリアル: ロード テストの作成および実行) を参照してください。

[プロパティ] ウィンドウの実行設定値の **[テスト イテレーション]** プロパティを編集するには、**ロード テスト エディター**を使用します。 **[テスト イテレーション]** プロパティでは、**ロード テスト エディター**を使用して、ロード テストのあらゆるシナリオで実行するすべての Web パフォーマンス テストと単体テストのイテレーションの回数を指定します。

> [!NOTE]
> 実行設定の各プロパティとその説明の一覧については、「[Load Test Run Settings Properties](../test/load-test-run-settings-properties.md)」(ロード テストの実行設定のプロパティ) を参照してください。


## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>実行設定でテスト イテレーションの回数を指定するには

1.  ロード テストを開きます。

     **[ロード テスト エディター]** が表示され、ロード テスト ツリーが表示されます。

2.  ロード テスト ツリーの **[実行設定]** フォルダーで、実行設定を選択します。

3.  **[表示]** メニューで、**[プロパティ ウィンドウ]** を選択し、ロードの実行設定のカテゴリとプロパティを表示します。

4.  **[テスト イテレーションの使用]** プロパティを **[True]** に設定します。

5.  **[テスト イテレーション]** プロパティで、ロード テスト中に実行するテスト イテレーションの回数を入力します。

6.  プロパティを変更したら、**[ファイル]** メニューの **[保存]** を選択します。 次に、新しい **[テスト イテレーション]** の値を使用して、ロード テストを実行します。

## <a name="see-also"></a>関連項目

- [ロード テストの実行設定の構成](../test/configure-load-test-run-settings.md)
- [ロード テスト シナリオのプロパティ](../test/load-test-scenario-properties.md)