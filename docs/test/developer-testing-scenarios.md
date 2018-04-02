---
title: Visual Studio の開発者用テスト ツール | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- unit testing, create unit tests
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ae3b475cb6f50f9c6ec623b7dfc588ada9b27163
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>開発者用テスト ツール、シナリオ、および機能

単体テストでコードの正常性を維持します。 Visual Studio では、開発者がアプリケーションをテストする際に使用する幅広い強力なツールと手法が提供されます。

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>IntelliTest で回帰を回避し、コード カバレッジを実現する

従来の単体テスト スイートでは、各テスト ケースで模範となる使用シナリオが示され、アサーションで入力と出力の関係が具体化されます。  内容は正しいもののテストされていない入力により間違った応答が返された場合、このようないくつかのシナリオを検証すれば十分かもしれませんが、経験豊富な開発者は十分テストされたコードでもバグが潜んでいることを認識しています。

IntelliTest でカバレッジを改善し、回帰を回避します。 IntelliTest によって、新規または既存のコードの単体テストを作成および保守する手間を大幅に削減できます。

![実行中の IntelliTest](media/devtest-intellitest.png)

* [Visual Studio での IntelliTest の概要](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest – 1 回のテストですべてのルールを把握](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx)
* [IntelliTest のビデオ](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [IntelliTest の概要](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest リファレンス マニュアル](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>コード化された UI と Selenium によるユーザー インターフェイスのテスト

最適に組み合わされた、またはコミュニティで承認された UI テストを使用して、ユーザー インターフェイス (UI) をテストします。
コード化された UI テストでは、アプリケーションのユーザー インターフェイスの機能と動作を検証するために完全に自動化されたテストを作成できます。
XAML ベースの UWP アプリ、ブラウザー アプリ、および SharePoint アプリなど、さまざまなテクノロジをカバーする UI テストを自動化できます。

コード化された UI テストまたは汎用ブラウザー ベースの UI テストと Selenium の最適な組み合わせを選択したかどうかに関係なく、Visual Studio では必要なツールがすべて提供されます。

![コード化された UI を使用した UI テスト](media/devtest-codeduitest.png)

* [UI オートメーションを使用してコードをテストする](use-ui-automation-to-test-your-code.md)
* [コード化された UI テストの作成、編集、および保守の概要](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [コード化された UI テストを使用して UWP アプリをテストする](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [コード化された UI テストを使用して Windows Phone アプリをテストする](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [コード化された UI テストを使用して SharePoint アプリケーションをテストする](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Visual Studio Enterprise でのコード化された UI テストの概要 (ラボ)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Visual Studio コード カバレッジでの効果的な単体テスト

単体テストなどのコード化されたテストによって実際にテストされるプロジェクトのコードの割合を調べる場合は、Visual Studio のコード カバレッジ機能を使用できます。 バグから効果的に保護するには、コードの大部分を "カバー" するようにテストを実行する必要があります。

コード カバレッジ分析は、マネージ コードにもアンマネージ (ネイティブ) コードにも適用できます。

コード カバレッジは、テスト エクスプローラーを使用してテスト メソッドを実行する場合のオプションです。 結果テーブルには、各アセンブリ、クラス、およびメソッドで実行されたコードの割合が表示されます。 また、ソース エディターには、どのコードがテストされたかが表示されます。

![Visual Studio Team Services と Team Foundation Server でテストする](media/devtest-codecoverage.png)

* [コード カバレッジを使用した、テストされるプロジェクトのコード割合の確認](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Visual Studio での単体テスト、コード カバレッジおよびコード クローン分析 (ラボ)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [コード カバレッジ分析のカスタマイズ](customizing-code-coverage-analysis.md)

## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>高パフォーマンス テスト エクスプローラーを使用する任意のフレームワークでの単体テスト

テスト エクスプローラーは、開発者が単体テストを作成し、管理して、最大限に活用できるようにします。

![Visual Studio テスト エクスプローラー](media/devtest-testexplorer.png)

* [単体テストの概要](unit-test-your-code.md)
* [テスト エクスプローラーを使用して単体テストを実行する](run-unit-tests-with-test-explorer.md)
* [C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)
* [サードパーティ製の単体テスト フレームワークをインストールする](install-third-party-unit-test-frameworks.md)

Visual Studio は拡張可能であり、NUnit や xUnit.net などのサード パーティの単体テスト アダプターにも対応します。 さらに、コード クローン機能では、一般的なバグの修正またはリファクタリングの対象になる可能性がある意味的に似たコードのブロックを特定できるようにして、高品質なソフトウェアを提供することもできます。

![サード パーティ テストの統合](media/devtest-thirdparty.png)

## <a name="see-also"></a>関連項目

* [単体テストの概要](getting-started-with-unit-testing.md)
* [Team Foundation Server での単体テストの実行の高速化](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx)
* [並列および状況依存の単体テストの実行](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Visual Studio での単体テスト、コード カバレッジおよびコード クローン分析 (ラボ)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
