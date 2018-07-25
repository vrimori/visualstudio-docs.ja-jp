---
title: Visual Studio での自動テストのための Test Controller および Test Agent に対するロールの割り当て
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f939947c4b96584439d85c33c234dc769531888d
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280612"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>ロールをテスト コントローラーとテスト エージェントに割り当てる

このチュートリアルでは、Visual Studio で、テスト コントローラーとテスト エージェントを使用して、複数のコンピューターにテストを分散するテスト設定の作成および構成手順について説明します。 また、診断およびデータ アダプターをテスト設定に追加する方法についても説明します。

このチュートリアルでは、次のタスクを行います。

-   テスト設定を作成する。

-   ロールをテスト コントローラーとテスト エージェントに割り当てる。

-   診断およびデータ アダプターをテスト設定に割り当てる。

## <a name="prerequisites"></a>必須コンポーネント

-   テスト設定で実行する単体テストまたはコード化された UI テストを作成する必要があります。

-   テスト コントローラーとテスト エージェントをインストールします。 テスト コントローラーとテスト エージェントをインストールする方法の詳細については、[テスト エージェントのインストールと構成](../test/lab-management/install-configure-test-agents.md)に関するページを参照してください。

## <a name="to-create-and-configure-a-test-setting"></a>テスト設定を作成および構成するには

1.  **ソリューション エクスプローラー**で、**[ソリューション項目]** を右クリックし、**[追加]** をポイントして、**[新しい項目]** を選択します。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2.  **[インストールされたテンプレート]** ペインで、**[テストの設定]** を選択します。

3.  **[名前]** ボックスに、「**TestSettingDistributedTestWalkthrough**」と入力します。

4.  **[追加]** をクリックします。

     **ソリューション エクスプローラー**の **[ソリューション項目]** フォルダーに、*TestSettingDistributedTestWalkthrough.testsettings* という新しいテスト ファイルが表示されます。

     **[テストの設定]** ダイアログ ボックスが表示されます。 **[全般]** ページが選択されています。

     このページで、テストの設定値を編集および保存できます。

    > [!NOTE]
    > 作成するそれぞれのテストの設定は、**[テスト]** メニューの **[アクティブなテスト設定の選択]** オプションおよび **[テスト設定の編集]** オプションに選択肢として一覧表示されます。

5.  **[名前]** ボックスに、テストの設定の名前を入力します。

6.  **[説明]** に、「**分散テスト設定**」と入力します。

7.  **[既定の名前付けスキーム]** が選択された状態のままにします。

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>ロールをテスト コントローラーとテスト エージェントに割り当てるには

1.  **[ロール]** を選択します。

     **[ロール]** ページが表示されます。

2.  テストをリモートで実行するには、**[テストの実行メソッド]** ドロップダウン リストの **[リモート実行]** をクリックします。

3.  **[コントローラー]** ドロップダウン リストに、[テスト コントローラー](../test/lab-management/install-configure-test-agents.md)のコンピューター名を入力します。

    > [!NOTE]
    > 初めてコントローラーを追加する場合、このドロップダウン リストにコントローラーは表示されません。 このリストは、他のテスト設定でそれまでに指定したコントローラーによって設定されます。

4.  **[ロール]** の **[追加]** をクリックします。

5.  **[名前]** 列の強調表示された行に、「**分散テスト**」と入力します。

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>診断およびデータ アダプターをテスト設定に割り当てるには

1.  **[データと診断]** を選択します。

     **[データと診断]** ページが表示されます。

2.  **[ロール]** で、**分散テスト** ロールが選択されていることを確認します。

3.  **[選択されたロールのデータと診断]** の **[IntelliTrace]** アダプターと **[システム情報]** アダプターを選択します。

     これらのアダプター、およびテストの設定で使用できるその他のアダプターの詳細については、[単体テストの構成](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)に関するページを参照してください。

4.  **[ホスト]** を選択します。

5.  (省略可能) コンピューターで 64 ビット バージョンの Microsoft Windows を実行しており、**Any CPU** 構成を使用してテストをコンパイルした場合は、**[32 ビット プロセスまたは 64 ビット プロセスでテストを実行]** ドロップダウン リストの **[64 ビット コンピューター上で 64 ビット プロセスでテストを実行]** をクリックします。

    > [!TIP]
    > 柔軟性を最大限に高めるには、テスト プロジェクトを**任意の CPU** 構成でコンパイルします。 これにより、32 ビット エージェントと 64 ビット エージェントの両方で実行できます。 **64 ビット**構成でテスト プロジェクトをコンパイルしても、特に利点はありません。

6.  新しいテストの設定を保存するには、**[適用]** をクリックします。

7.  **[閉じる]** を選択します。

8.  [テスト] メニューの **[アクティブなテスト設定の選択]** をクリックし、**[TestSettingDistributedTestWalkthrough.testsettings]** をクリックします。

9. 通常どおり、テストを実行します。

     テスト コントローラーは、単体テストおよびコード化された UI テストを処理するとき、テストを 100 個単位のグループに分割し、テスト エージェント コンピューターに送信します。 たとえば、250 個の単体テストと 3 つのテスト エージェントがある場合、最初の 100 個の単体テストは agent1 に送信され、次の 100 個の単体テストは agent2 に送信され、残りの 50 個の単体テストは agent3 に送信されます。

## <a name="see-also"></a>関連項目

- [テスト エージェントをインストールして構成する](../test/lab-management/install-configure-test-agents.md)