---
title: "テスト エクスプローラーに関する FAQ | Microsoft Docs"
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: db3cf85576e6c46aca14897f7244cd0f56d8d5c2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio テスト エクスプローラーに関する FAQ

## <a name="test-discovery"></a>テスト検出

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1.テスト エクスプローラーが、理論、カスタム アダプター、またはカスタムの特徴を持つテストや、#ifdefs を使用したり動的に定義されたテストを検出しません。 これらのテストを検出するにはどうすればよいですか?

  プロジェクトをビルドして、**[ツール] > [オプション] > [テスト]** の順に移動して、アセンブリベースの検出がオンになっていることを確認します。

  ソースベースのテストの検出である[リアルタイムのテスト検出](https://go.microsoft.com/fwlink/?linkid=862824)では、理論、カスタム アダプター、カスタムの特徴、`#ifdef` ステートメントを使用するテストや、他の何らかの方法で動的に定義されるテストを検出することはできません。 これらのテストを正確に検出するには、ビルドが必要です。 15.6 プレビューでは、アセンブリベースの検出 (従来の検出プログラム) はビルドの後にのみ実行されます。 つまり、リアルタイムのテスト検出は、ユーザーが編集中にできるだけ多くのテストを検出し、アセンブリベースの検出では、ビルド後に理論 (または動的に定義されたテスト) を表示できるようにします。 リアルタイムのテスト検出は、応答性を高めながら、ビルド後に完全かつ正確な結果を得ることができます。

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2.テスト エクスプローラーの最初の行に表示される '+' (プラス) 記号は何を意味しているのですか?

  '+' (プラス) 記号は、アセンブリベースの検出をオンにすると、ビルド後にさらに多くのテストが検出される可能性があることを示しています。 これは、プロジェクト内で動的に定義されているテストが検出されると表示されます。

  ![サマリー行のプラス記号](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3.プロジェクトでアセンブリベースの検出が機能しなくなりました。 元に戻すにはどうしたらよいですか?

  **[ツール] > [オプション] > [テスト]** の順に移動して、**[ビルド後にビルド済みアセンブリからテストをさらに探索する]** のチェック ボックスをオンにします。

  ![アセンブリベースのオプション](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4.プロジェクトをビルドしなくても、入力中にテストがテスト エクスプローラーに表示されるようになりました。 何か変更されたのでしょうか?

  この機能は、[リアルタイムのテスト検出](https://go.microsoft.com/fwlink/?linkid=862824)と呼ばれます。 これは Roslyn アナライザーを使用してテストを検出し、リアルタイムでテスト エクスプローラーに表示します。プロジェクトをビルドする必要はありません。 理論やカスタムの特徴などの動的に定義されたテストに対するテスト検出の動作の詳細については、FAQ #1 を参照してください。

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5.リアルタイムのテスト検出では、どの言語およびテスト フレームワークを使用できますか?

  [リアルタイムのテスト検出](https://go.microsoft.com/fwlink/?linkid=862824)は、Roslyn コンパイラを使用してビルドされているため、マネージ言語 (C# および Visual Basic) に対してのみ機能します。 今のところ、リアルタイムのテスト検出は xUnit、NUnit、MSTest のフレームワークに対してのみ機能します。

## <a name="features"></a>フィーチャー

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>新しいテスト機能を試すために機能フラグをオンにするにはどうしたらよいですか?

機能フラグは、機能を公式に出荷する前に、フィードバックを提供する熱心なユーザー向けに、製品の実験用または未完成部分を出荷するために使用されます。 これは IDE エクスペリエンスの安定性を損なう可能性があります。 仮想マシンなどの安全な開発環境でのみ使用することをお勧めします。 機能フラグの設定は、常に各自の責任で行ってください。 実験用の機能は、[機能フラグの拡張機能](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)を使用するか、開発者コマンド プロンプトを使用してオンにすることができます。

![機能フラグの拡張機能](media/testex-featureflag.png)

Visual Studio 開発者コマンド プロンプトで機能フラグをオンにするには、次のコマンドを使用します。 パスを Visual Studio がインストールされているコンピューターに変更し、レジストリ キーを目的の機能フラグに変更します。

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> dword の後の値を 1 ではなく 0 にすると、同じコマンドでフラグをオフにできます。
  
## <a name="see-also"></a>関連項目

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[既存コードに対する単体テストの作成と実行](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[コードの単体テスト](unit-test-your-code.md)
[Live Unit Testing についてよく寄せられる質問](live-unit-testing-faq.md)
