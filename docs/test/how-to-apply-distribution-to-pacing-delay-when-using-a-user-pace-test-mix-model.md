---
title: ロード テストのために遅延のペースに分布を適用する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 758e07ba6fae2d06d72f9a2df98a2e78b6e2284a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917927"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>方法: ユーザー ペースのテスト ミックス モデルに対する遅延のペースに分布を適用する

**新しいロード テスト ウィザード**でロード テストを作成した後、ロード テスト エディターを使用して、テストのニーズや目標に合わせてシナリオのプロパティを変更できます。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**[遅延のペースに分布を適用]** プロパティは、**[プロパティ]** ウィンドウを使用して設定します。 ロード テスト シナリオの各プロパティは後でロード テスト エディターを使用して変更します。

> [!NOTE]
> **"遅延のペースに分布を適用"** プロパティは、*ロード テスト ミックス*がユーザーのペースに基づいて構成されている場合にのみ適用されます。 詳細については、「[テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定する](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

**"遅延のペースに分布を適用"** の値は、true または false に設定できます。

- **True**:**[テスト ミックスの編集]** ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** 列の値で指定された、標準的な統計分布による遅れを適用します。 詳細については、「[テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定する](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

     たとえば、テストの **[テスト ミックスの編集]** ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** の値を、1 時間あたり 2 ユーザーに設定したとします。 **"遅延のペースに分布を適用"** プロパティを **True** に設定すると、標準的な統計分布がテスト間の待機時間に適用されます。 1 時間につき 2 つのテストが実行されますが、その間隔は 30 分とは限りません。 最初のテストが 4 分後に実行されたり、2 回目のテストが 45 分後に実行されたりする場合があります。

- **False**:**[テスト ミックスの編集]** ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** 列の値に指定したペースでテストを実行します。 詳細については、「[テキスト ミックス モデルを編集して仮想ユーザーがテストを実行する確率を指定する](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)」を参照してください。

     たとえば、テストの **[テスト ミックスの編集]** ダイアログ ボックスの **[1 ユーザーの 1 時間あたりのテスト数]** の値を、1 時間あたり 2 ユーザーに設定したとします。 **"遅延のペースに分布を適用"** プロパティを **False** に設定すると、テスト実行時の設定を変更する余裕はなくなります。 テストは 30 分ごとに実行されます。 これにより、1 時間あたり 2 回のテストが行われます。

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>シナリオの "遅延のペースに分布を適用" プロパティの設定を指定するには

1. ロード テストを開きます。

   **ロード テスト エディター**が表示されます。 ロード テスト ツリーが表示されます。

2. ロード テスト ツリーの **[シナリオ]** フォルダーで、ペースの分布を適用するシナリオ ノードを選びます。

3. **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。

   **[プロパティ]** ウィンドウに、シナリオのカテゴリおよびプロパティが表示されます。

4. **"遅延のペースに分布を適用"** のプロパティ値で、**True** または **False** を選択します。

5. **[ファイル]** > **[保存]** を選びます。 次に、**[遅延のペースに分布を適用]** の新しい値を使用して、ロード テストを実行します。

## <a name="see-also"></a>関連項目

- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)
- [チュートリアル: ロード テストの作成および実行](../test/walkthrough-create-and-run-a-load-test.md)
- [テスト コントローラーとテスト エージェント](configure-test-agents-and-controllers-for-load-tests.md)
- [ロード テスト シナリオのプロパティ](../test/load-test-scenario-properties.md)