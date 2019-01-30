---
title: テスト用ツール
ms.date: 03/16/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 12089bf5033ed126558fb2e859a3132aecd0cde5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972496"
---
# <a name="testing-tools-in-visual-studio"></a>Visual Studio のテスト ツール

Visual Studio のテスト ツールを使用することで、チームと共に高水準の優れたコードを開発し、維持できます。

- **テスト エクスプローラー** ウィンドウを使用すると、開発の手法において[単体テスト](../test/unit-test-your-code.md)を容易に統合できるようになります。 Microsoft 単体テスト フレームワークまたは複数のサードパーティ フレームワークやオープン ソース フレームワークの 1 つを使用できます。

- [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) は、マネージド コードの単体テストとテスト データを自動生成します。

- [コード カバレッジ](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)は、プロジェクトのコードの中で、単体テストなどのコード化されたテストによって実際にテストされる割合を判断します。

- [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) では、アプリケーションの別の部分をスタブまたは shim で置き換えることにより、テストするコードを分離できます。

- [Live Unit Testing](../test/live-unit-testing.md) は、バックグラウンドで自動的に単体テストを実行し、Visual Studio のコード エディターにコード カバレッジとテスト結果をグラフィカルに表示します。

- [コード化された UI テスト](../test/use-ui-automation-to-test-your-code.md)を利用し、ユーザー インターフェイスを介してアプリケーションをテストします。

- [ロード テスト](../test/quickstart-create-a-load-test-project.md)では、単体テストと Web パフォーマンス テストを実行することでサーバー アプリケーションの負荷をシミュレーションします。

> [!NOTE]
> 単体テストは、Visual Studio のすべてのエディションで使用できます。 ライブ単体テスト、IntelliTest、コード化された UI テストなど、その他のテスト ツールは Visual Studio Enterprise エディションでのみ使用できます。 エディションの詳細については、「[Visual Studio 2017 IDE の比較](https://visualstudio.microsoft.com/vs/compare/)」を参照してください。

## <a name="related-scenarios"></a>関連するシナリオ

* [探索的テストと手動テスト (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [ロード テスト (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [継続的なテスト (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [コード分析ツール](../code-quality/code-analysis-for-managed-code-overview.md)
