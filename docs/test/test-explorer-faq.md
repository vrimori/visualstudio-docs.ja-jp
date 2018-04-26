---
title: Visual Studio テスト エクスプローラーに関する FAQ
ms.date: 1/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: douge
ms.openlocfilehash: 151f60d21914168ea62bdb2d978d93839c8b859b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio テスト エクスプローラーに関する FAQ

## <a name="test-discovery"></a>テスト検出

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1.テスト エクスプローラーが、動的に定義されたテストを検出しません (理論、カスタム アダプター、カスタム特性、#ifdefs など)。これらのテストを検出するにはどうすればよいですか?

  プロジェクトをビルドして、**[ツール] > [オプション] > [テスト]** の順に移動して、アセンブリベースの検出がオンになっていることを確認します。

  [リアルタイムのテスト検出](https://go.microsoft.com/fwlink/?linkid=862824)は、ソース ベースのテストの検出です。 理論、カスタム アダプター、カスタム特性、`#ifdef` ステートメントなどは実行時に定義されるため、これらを使うテストは検出できません。 これらのテストを正確に検出するには、ビルドが必要です。 15.6 プレビューでは、アセンブリベースの検出 (従来の検出プログラム) はビルドの後にのみ実行されます。 この設定は、リアルタイムのテスト検出は、ユーザーが編集中にできるだけ多くのテストを検出し、アセンブリベースの検出では、ビルド後に動的に定義されたテストを表示できるようにすることを意味します。 リアルタイムのテスト検出は、応答性を高めながら、ビルド後に完全かつ正確な結果を得ることができます。

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2.テスト エクスプローラーの最初の行に表示される '+' (プラス) 記号は何を意味しているのですか?

  "+" (プラス) 記号は、アセンブリベースの検出がオンになっていると、ビルド後にさらに多くのテストが検出される可能性があることを示しています。 これは、プロジェクト内で動的に定義されているテストが検出されると表示されます。

  ![サマリー行のプラス記号](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3.プロジェクトでアセンブリベースの検出が機能しなくなりました。 元に戻すにはどうしたらよいですか?

  **[ツール] > [オプション] > [テスト]** の順に移動して、**[ビルド後にビルド済みアセンブリからテストをさらに探索する]** チェック ボックスをオンにします。

  ![アセンブリベースのオプション](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4.プロジェクトをビルドしなくても、入力中にテストがテスト エクスプローラーに表示されるようになりました。 何か変更されたのでしょうか?

  この機能は、[リアルタイムのテスト検出](https://go.microsoft.com/fwlink/?linkid=862824)と呼ばれます。 これは Roslyn アナライザーを使用してテストを検出し、リアルタイムでテスト エクスプローラーに表示します。プロジェクトをビルドする必要はありません。 理論やカスタムの特徴などの動的に定義されたテストに対するテスト検出の動作については、FAQ #1 を参照してください。

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5.リアルタイムのテスト検出では、どの言語およびテスト フレームワークを使用できますか?

  [リアルタイムのテスト検出](https://go.microsoft.com/fwlink/?linkid=862824)は、Roslyn コンパイラを使用してビルドされているため、マネージ言語 (C# および Visual Basic) に対してのみ機能します。 今のところ、リアルタイムのテスト検出は xUnit、NUnit、MSTest のフレームワークに対してのみ機能します。

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6.どうすればテスト エクスプローラーのログを有効にできますか?

  **[ツール] > [オプション] > [テスト]** の順に移動し、そこで [ログ] セクションを見つけます。

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7.アプリを配置するまで UWP プロジェクトのテストが検出されないのはなぜですか?

  アプリが配置されると、UWP テストは異なるランタイムを対象にします。 つまり、UWP プロジェクトで正確にテストを検出するには、プロジェクトをビルドするだけでなく、配置することも必要です。

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8.階層ビューでテスト結果を並べ替えるにはどうすればよいですか?

  階層ビューでは、結果順ではなくアルファベット順にテストが並べ替えられます。 通常、他のグループ化設定は、テスト結果を結果順に並べ替えてからアルファベット順に並べ替えます。 次の比較図で、オプションによるグループの違いを確認してください。 [この GitHub の問題で](https://github.com/Microsoft/vstest/issues/1425)設計に関するフィードバックを提供できます。

  ![SortingExamples](media/testex-sortingex.png)

### <a name="9-in-the-hierarchy-view-there-are-passed-failed-skipped-and-not-run-icons-next-to-the-project-namespace-and-class-groupings-what-do-these-icons-mean"></a>9.階層ビューに、プロジェクト、名前空間、およびクラス グループの横に、合格、失敗、省略、および未実行アイコンがあります。 これらのアイコンの意味を教えてください。

  プロジェクト、名前空間、およびクラス グループの横にあるアイコンは、そのグループ内のテストの状態を反映します。 次の表を参照してください。

  ![テスト エクスプローラーの階層のアイコン](media/testex-hierarchyicons.png)
  
### <a name="10-there-is-no-longer-a-file-path-filter-in-the-test-explorer-search-box"></a>10.テスト エクスプローラーの検索ボックスの "ファイル パス" フィルターはもう存在しません。

**テスト エクスプローラー**の検索ボックスのファイル パス フィルターは、Visual Studio 2017 バージョン 15.7 プレビュー 3 で削除されました。 この機能は使用頻度が低く、この機能を除外することで、テスト エクスプローラーはテスト メソッドを高速で取得できます。 この変更によって開発フローが中断される場合は、[開発者コミュニティ](https://developercommunity.visualstudio.com/)でフィードバックを送信してその旨をお知らせください。

## <a name="features"></a>フィーチャー

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>新しいテスト機能を試すために機能フラグをオンにするにはどうしたらよいですか?

機能フラグは、機能を公式に出荷する前に、フィードバックを提供する熱心なユーザー向けに、製品の実験用または未完成部分を出荷するために使用されます。 これは IDE エクスペリエンスの安定性を損なう可能性があります。 仮想マシンなどの安全な開発環境でのみ使用してください。 機能フラグの設定は、常に各自の責任で行ってください。 実験用の機能は、[機能フラグの拡張機能](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)を使用するか、開発者コマンド プロンプトを使用してオンにすることができます。

![機能フラグの拡張機能](media/testex-featureflag.png)

Visual Studio 開発者コマンド プロンプトで機能フラグをオンにするには、次のコマンドを使用します。 パスを Visual Studio がインストールされているコンピューターに変更し、レジストリ キーを目的の機能フラグに変更します。

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> dword の後の値を 1 ではなく 0 にすると、同じコマンドでフラグをオフにできます。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [既存コードに対する単体テストの作成と実行](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [コードの単体テスト](unit-test-your-code.md)
- [ライブ単体テストに関する FAQ](live-unit-testing-faq.md)
