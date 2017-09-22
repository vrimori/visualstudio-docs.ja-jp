---
title: "Visual Studio の Python 用単体テスト | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3ad6523-5a4e-4209-8977-adc2da305df2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: e48ebcafaca37505dbcc92bce682d0c6169004e1
ms.openlocfilehash: b68dc3d2fb7877349fc319ce5ea6e799f80c1dbf
ms.contentlocale: ja-jp
ms.lasthandoff: 07/26/2017

---

# <a name="setting-up-unit-testing-for-python-code"></a>Python コードの単体テストの設定

単体テストは、アプリケーションの他のコード単位 (通常は分離された関数、クラスなど) をテストするコードの断片です。 アプリケーションがそのすべての単体テストに合格すると、少なくとも低レベルの機能が正しいことを信頼できます。

Python は、プログラムの設計時にシナリオを検証するために単体テストを幅広く使用します。 Visual Studio の Python サポートには、別々にテストを実行する必要のない、開発プロセスのコンテキスト内での単体テストの検出、実行、デバッグのサポートが含まれています。

このトピックでは、Python での Visual Studio の単体テスト機能の概要を説明します。 一般的な単体テストについて詳しくは、「[コードの単体テスト](../test/unit-test-your-code.md)」をご覧ください。

## <a name="discovering-and-viewing-tests"></a>テストの検出と表示

規則により、Visual Studio はテストをその名前が `test` で始まるメソッドとして識別します。 この動作を確認するには、次の操作を行います。

1. Visual Studio に読み込まれた [Python プロジェクト](python-projects.md)を開き、プロジェクトを右クリックして **[追加] > [新しい項目...]** を選択し、**[Python Unit Test (Python 単体テスト)]** に続けて **[追加]** を選択します。

1. この操作で、標準 `unittest` モジュールをインポートし、`unittest.TestCase` からテスト クラスを派生させ、スクリプトを直接実行する場合に `unittest.main()` を起動するコードを含む `test1.py` ファイルが作成されます。

  ```python
  import unittest

  class Test_test1(unittest.TestCase):
      def test_A(self):
          self.fail("Not implemented")

  if __name__ == '__main__':
      unittest.main()
  ```

1. 必要に応じてファイルを保存し、**[テスト] > [Windows] > [テスト エクスプローラー]** メニュー コマンドでテスト エクスプローラーを開きます。

1. テスト エクスプローラーは、テストするプロジェクトを検索し、それらを次のように表示します。 テストをダブルクリックすると、そのソース ファイルが開きます。

    ![既定の test_A を表示しているテスト エクスプローラー](media/unit-test-A.png)

1. 他のテストをプロジェクトに追加すると、ツール バーのグループ化メニューを使用してテスト エクスプローラーのビューを整理できます。

    ![テスト エクスプローラーのグループ化ツール バー メニュー](media/unit-test-group-menu.png)

1. 検索フィールドにテキストを入力してテストを名前でフィルター処理することもできます。

`unittest` モジュールとテストの記述について詳しくは、[Python 2.7 ドキュメント](https://docs.python.org/2/library/unittest.html)または [Python 3.4 ドキュメント](https://docs.python.org/3/library/unittest.html) (python.org) をご覧ください。

## <a name="running-tests"></a>テストの実行

テスト エクスプローラーでは、さまざまな方法でテストを実行できます。

- **[Run All (すべて実行)]** は、表示されているすべてのテスト (フィルターの対象) を明確に実行します。
- **[実行...]** メニューには、失敗、合格、または未実行のテストをグループとして実行するコマンドが用意されています。
- 1 つ以上のテストを選んで右クリックし、**[選択したテストの実行]** を選択します。

テストはバックグラウンドで実行され、完了するとテスト エクスプローラーが各テストの状態を更新します。

- 合格したテストには、緑のチェックマークとテストの実行にかかった時間が表示されます。

    ![test_A の合格状態](media/unit-test-A-pass.png)

- 失敗したテストには、コンソール出力とテストの実行からの `unittest` 出力を示す **[出力]** リンクとともに赤い × 印が表示されます。

    ![test_A の失敗状態](media/unit-test-A-fail.png)

    ![test_A の失敗とその理由](media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>テストのデバッグ

単体テストはコードの断片であるため、他のコードと同様にバグが発生することがあり、デバッガーでの実行が必要になることがあります。 デバッガーでは、ブレークポイントを設定し、変数を確認し、コードをステップ実行することができます。 Visual Studio には単体テストのための診断ツールも用意されています。

デバッグを開始するには、コードに最初のブレークポイントを設定し、テスト エクスプローラーでテスト (または選択範囲) を右クリックし、**[選択したテストのデバッグ]** を選択します。 アプリケーション コードの場合と同様に、Visual Studio が Python デバッガーを起動します。

![テストのデバッグ](media/unit-test-debugging.png)

Visual Studio のバージョンに応じて、**[選択されたテストのコード カバレッジの分析]** コマンドと **[テストのプロファイル]** コマンドを使用することもできます ([機能のマトリックス](python-in-visual-studio.md#features-matrix)のページをご覧ください)。

### <a name="known-issues"></a>既知の問題

- デバッグを開始するときに、Visual Studio がデバッグを起動して停止してからもう一度開始するように見えます。 この動作は想定内です。
- 複数のテストをデバッグするときに、それぞれが個別に実行され、デバッグ セッションが中断されます。
- Visual Studio で、デバッグ時にテストの開始が断続的に失敗します。 通常は、もう一度テストをデバッグしようとすると成功します。
- デバッグ時に、テストを `unittest` 実装にステップ アウトできます。 通常は、次のステップはプログラムの最後まで実行されてデバッグを停止します。
