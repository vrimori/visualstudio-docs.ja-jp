---
title: Visual Studio での単体テストの概要
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 761f814d3a224240c27fa6b058fb08325f0307f4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177868"
---
# <a name="get-started-with-unit-testing"></a>単体テストの概要

Visual Studio を使用して、単体テストを定義および実行してコードの正常性を維持し、コード カバレッジを保証し、事前にエラーとフォールトを見つけます。

## <a name="create-unit-tests"></a>単体テストの作成

単体テストを作成し、コードが正しく動作していることを確認するために頻繁に実行します。

1. 単体テスト プロジェクトを作成します。

   ![単体テスト プロジェクトをソリューションに追加する](media/createunittest1.png)

1. プロジェクトに名前を付けます。

   ![単体テスト プロジェクト テンプレート](media/createunittest2.png)

   プロジェクトがソリューションに追加されます。

   ![ソリューション エクスプローラーの単体テスト プロジェクト](media/createunittest5.png)

1. 単体テスト プロジェクトで、テストするプロジェクトに参照を追加します。

   ![単体テストプロジェクトへの参照を追加する](media/createunittest6.png)

1. テストするコードを含むプロジェクトを選択します。

   ![追加する参照を選択する](media/createunittest7.png)

1. 単体テストのコードを作成します。

   ![コードを単体テストに追加する](media/createunittest8.png)

**[単体テストの作成]** [コマンド](create-unit-tests-menu.md)を使用して、単体テスト メソッド スタブを作成することもできます。

![[単体テストの作成] コマンドの使用](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>単体テストを実行する

1. **テスト エクスプローラー**を開きます。

   ![[テスト] メニューで、テスト エクスプローラーを開く](media/rununittest1.png)

1. 単体テストを実行します。

   ![テスト エクスプローラーでの単体テストの実行](media/rununittest2.png)

   **テスト エクスプローラー**に成功または失敗した単体ユニット テストが表示されます。

   ![テスト エクスプローラーで単体テストの結果を確認する](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>ライブ単体テストの結果を表示する

Visual Studio 2017 以降で MSTest、xUnit、または NUnit テスト フレームワークを使用する場合は、単体テストのライブ結果を表示できます。

> [!NOTE]
> Visual Studio 2017 Enterprise Edition では、ライブ単体テストを使用できます。

1. **[テスト]** メニューで、ライブ単体テストをオンにします。

   ![ライブ単体テストをオンにする](media/live-test-results-start.png)

1. コードの作成および編集時に、コード エディター ウィンドウ内でテストの結果を表示します。

   ![テスト結果を表示する](media/live-test-results-ui.png)

1. テスト結果インジケーターを選択すると、詳細が表示されます。

   ![テスト結果インジケーターを選択します。](media/live-test-results-details.png)

詳細については、[ライブ単体テスト](../test/live-unit-testing-intro.md)に関するページを参照してください。

## <a name="generate-unit-tests-with-intellitest"></a>IntelliTest で単体テストを生成する

IntelliTest を実行すると、どのテストが失敗しているかを簡単に把握し、必要なコードを追加して修正できます。 回帰スイートを提供するために、生成されたどのテストをテスト プロジェクトに保存するかを選択できます。 コードを変更する際に、IntelliTest を再実行して、生成されたテストとコードの変更を同期させます。 その方法については、「[IntelliTest でのコードの単体テストの生成](../test/generate-unit-tests-for-your-code-with-intellitest.md)」を参照してください。

![IntelliTest での単体テストの生成](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>テスト エクスプローラーを使用して単体テストを実行する

**テスト エクスプローラー**を使用して、Visual Studio またはサードパーティの単体テスト プロジェクトから単体テストを実行し、テストをカテゴリにグループ化し、テスト リストをフィルター処理し、テストのプレイリストを作成、保存、および実行します。 テストをデバッグし、テストのパフォーマンスとコード カバレッジを分析することもできます。 その方法については、「[テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)」を参照してください。

![テスト エクスプローラーを使用した単体テストの実行](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>コード カバレッジを使用した、テストされるコード割合の確認

単体テストなどのコード化されたテストによって実際にテストされるプロジェクトのコードの割合を調べるには、Visual Studio のコード カバレッジ機能を使用できます。 バグから効果的に保護するには、コードの大部分を "カバー" するようにテストを実行する必要があります。 その方法については、「[コード カバレッジを使用した、テストされるプロジェクトのコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)」を参照してください。

![コード カバレッジを使用した、テストされるコード割合の確認](media/codecoverage.png)

## <a name="use-a-different-unit-test-framework"></a>別の単体テスト フレームワークを使用する

Boost、Google、nUnit など、サードパーティのテスト フレームワークを利用し、Visual Studio で単体テストを実行できます。 Visual Studio のテスト ランナーがそのフレームワークで作業できるようにそのフレームワークのプラグインを使用します。

以下は、サードパーティのテスト フレームワークを有効にする手順です。

1. メニュー バーで **[ツール]** > **[拡張機能と更新プログラム]** の順に選択します。

1. **[拡張機能と更新プログラム]** ダイアログ ボックスで **[オンライン]** カテゴリを展開し、**[Visual Studio Marketplace]** を選択します。 **[ツール]**、 > **[テスト]** の順に選択します。

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. インストールするフレームワークまたはアダプターを選択し、**[ダウンロード]** を選択します。

1. クラス ライブラリ プロジェクトを作成し、ソリューションに追加します。

   ![クラス ライブラリ プロジェクトに名前を付けて追加する](media/create3rdpartyunittest3.png)

1. プラグインをインストールします。 **ソリューション エクスプローラー**で、クラス ライブラリ プロジェクトを選択し、その右クリック メニューまたはコンテキスト メニューから **[NuGet パッケージの管理]** を選択します。

   ![プラグインをインストールするための [NuGet パッケージの管理]](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) はプロジェクトのライブラリとツールの追加および更新に使用できる Visual Studio の拡張機能です。

1. **[NuGet パッケージ マネージャー]** ウィンドウで、プラグインを探して選択し、**[インストール]** を選択します。

   ![サード パーティのフレームワークをインストールする](media/create3rdpartyunittest4.png)

   フレームワークはプロジェクトで参照されます。

   ![サード パーティの単体テスト フレームワークの参照がソリューションに追加されている](media/create3rdpartyunittest6.png)

1. クラス ライブラリ オブジェクトの **[参照]** ノードから **[参照の追加]** を選択します。

   ![プロジェクトに参照を追加する](media/createunittest6.png)

1. **[参照マネージャー]** ダイアログ ボックスで、テストするコードが含まれるプロジェクトを選択します。

   ![テストするコード プロジェクトを選択する](media/createunittest7.png)

1. 単体テストのコードを作成します。

   ![コードを単体テストに追加する](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>関連項目

* [単体テスト コマンドの作成](create-unit-tests-menu.md)
* [IntelliTest でのテストの生成](generate-unit-tests-for-your-code-with-intellitest.md)
* [テスト エクスプローラーを使用してテストを実行する](run-unit-tests-with-test-explorer.md)
* [コード カバレッジを確認する](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [コード品質の向上](improve-code-quality.md)