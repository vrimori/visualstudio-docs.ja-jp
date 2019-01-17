---
title: 単体テスト
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1b036a9a34711d82194ea3c41acdb12651978446
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868642"
---
# <a name="unit-test-your-code"></a>コードの単体テスト

単体テストを実行することにより、開発者およびテスト担当者は、C#、Visual Basic、C++ のプロジェクトでクラスのメソッドに論理エラーがないかどうかをすばやく確認できます。

単体テスト ツールには次の要素が含まれます。

* **テスト エクスプローラー**&mdash;単体テストを実行して、**テスト エクスプローラー**でその結果を確認できます。 サードパーティ製のフレームワークを含めて、**テスト エクスプローラー**のアダプターがあるすべての単体テスト フレームワークを使用できます。

* **マネージド コード用の Microsoft 単体テスト フレームワーク**&mdash;マネージド コード用の Microsoft 単体テスト フレームワークは、Visual Studio と共にインストールされ、.NET コードをテストするためのフレームワークを提供します。

* **C++ 用の Microsoft 単体テスト フレームワーク**&mdash;C++ 用の Microsoft 単体テスト フレームワークは、**C++ によるデスクトップ開発**ワークロードの一部としてインストールされます。 これにより、ネイティブ コードをテストするためのフレームワークが提供されます。 Google Test、Boost.Test、CTest の各フレームワークも含まれており、サードパーティ製のアダプターを追加のテスト フレームワークで使用できます。 詳細については、[C/C++ 用の単体テストの作成](../test/writing-unit-tests-for-c-cpp.md)に関するページを参照してください。

* **コード カバレッジ ツール**&mdash; テスト エクスプローラーで、単体テストが 1 つのコマンドから実行する製品コードの量を確認できます。

* **Microsoft Fakes 分離フレームワーク**&mdash; Microsoft Fakes 分離フレームワークによって、テスト対象コード内の依存関係を作成する実稼働コードおよびシステム コード向けの代替クラスおよび代替メソッドを作成できます。 関数の Fake デリゲートを実装して、依存関係オブジェクトの動作と出力を制御します。

また、[IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) を使用して .NET コードを確認し、テスト データと単体テストのスイートを生成することもできます。 コードにある各ステートメントについて、そのステートメントを実行するテスト入力が生成されます。 コード内の各条件付き分岐について、ケース分析が実行されます。

## <a name="key-tasks"></a>主なタスク

単体テストを理解および作成するには、次のトピックを参照してください。

|[タスク]|関連するトピック|
|-|-----------------------|
|**クイック スタートおよびチュートリアル:** 次のトピックでは、Visual Studio での単体テストについてコード例から学習できます。|-   [チュートリアル: マネージド コードに対する単体テストの作成と実行](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [クイック スタート: テスト エクスプローラーによるテスト駆動開発](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [既存の C++ アプリケーションへの単体テストの追加](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**テスト エクスプローラーによる単体テスト:** テスト エクスプローラーによって、さらに生産性が高く効率的な単体テストを作成できることを学習します。|-   [単体テストの基本](../test/unit-test-basics.md)<br />-   [単体テスト プロジェクトを作成する](../test/create-a-unit-test-project.md)<br />-   [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)<br />-   [サードパーティ製の単体テスト フレームワークをインストールする](../test/install-third-party-unit-test-frameworks.md)|
|**C++ コードの単体テスト**|-   [C++ 用の Microsoft 単体テスト フレームワークを使用した C/C++ 用単体テストの記述](../test/writing-unit-tests-for-c-cpp.md)|
|**単体テストの分離**|-   [Microsoft Fakes を使用したテストでコードを分離する](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**コード カバレッジを使用してテストされるプロジェクトのコードの割合を識別する:** Visual Studio のテスト ツールのコード カバレッジ機能について説明します。|-   [コード カバレッジを使用した、テストされるコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**ロード テストを使用したストレスおよびパフォーマンスの分析の実行:** ロード テストを作成し、それに単体テストを追加すると、アプリケーションのパフォーマンスおよびストレスの問題を分離するのに役立ちます。|-   [ロード テスト (Azure Test Plans と TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**品質ゲートの設定:** 品質ゲートを作成し、コードがチェックインまたはマージされる前にテストを実行することで、コードの品質を保証できます。|-   [チェックイン ポリシー (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**テストのオプションを設定する:** たとえば、テスト結果が格納される場所を指定できます。|[.runsettings ファイルを使用して単体テストを構成する](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API リファレンス ドキュメント

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> では、UnitTesting 名前空間について説明します。この名前空間は、単体テストをサポートする属性、例外、アサートなどのクラスを提供します。
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> では、UnitTesting.Web 名前空間について説明します。この名前空間は、ASP.NET および Web サービスの単体テスト サポートを提供することで UnitTesting 名前空間を拡張します。

## <a name="see-also"></a>関連項目

- [コード品質の向上](../test/improve-code-quality.md)
