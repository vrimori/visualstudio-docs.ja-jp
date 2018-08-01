---
title: Visual Studio でロード テスト用のカウンター セット マップにコンピューター タグを追加する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 96ce122c78c20b741613ed45820f585236a0383b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203668"
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>方法: ロード テスト エディターを使用してコンピューター タグをカウンター セットのマップに追加する

コンピューター タグを使用すると、わかりやすい名前でコンピューターを識別できます。 このタグは、ロード テスト エディターのツリーの **[カウンター セットの割り当て]** ノードに表示されます。 また、このタグは Excel のレポートにも表示されるため、関係者がロード テストでコンピューターのロールを確認する際に役立ちます。 たとえば、"ラボ 2 の Web サーバー 1" や "Phoenix オフィスの SQL Server 2" のようなタグを使用できます。 詳細については、「[テストの比較または傾向分析に備えたロード テストの結果レポートの作成](../test/compare-load-test-results.md)」を参照してください。

## <a name="to-add-a-tag-to-a-computer"></a>コンピューターにタグを追加するには

1.  ロード テストを開きます。

2.  **[カウンター セットの管理]** ボタンを選択します。

     または

     ロード テスト ツリーで **[カウンター セット]** フォルダーを右クリックし、**[カウンター セットの管理]** を選択します。

     **[カウンター セットの管理]** ダイアログ ボックスが表示されます。

3.  (省略可能) **[選択されたコンピューターおよびカウンター セットは、次の実行設定で追加されます]** リスト ボックスで、別の実行設定を選択します。

    > [!NOTE]
    > この手順は、ロード テストに複数の実行設定がある場合にのみ適用されます。

4.  **[監視するコンピューターおよびカウンター セット]** で、タグを適用するコンピューターを選択します。

    > [!NOTE]
    > コンピューターの追加方法の詳細については、「[方法: カウンター セットを管理する](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)」を参照してください。

5.  **[コンピューター タグ]** ボックスに、コンピューターに関連付けるタグを入力します。 たとえば、「ラボ 3 の TestMachine12」のように入力します。

6.  **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [しきい値規則違反](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [ロード テストでのコンピューターのカウンター セットとしきい値規則の指定](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [方法: カウンター セットを管理する](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)