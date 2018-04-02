---
title: .NET 開発者向けの Visual Studio 2017 | Microsoft Docs
description: .NET コードをより速く記述するための Visual Studio 2017 の機能の概要。
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>.NET 開発者のための Visual Studio 2017 生産性ガイド

- [生産性ガイド](#guide)
- [Visual Studio 2017 の概要](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/> 生産性ガイド
[Visual Studio 2017](https://www.visualstudio.com/downloads/) を使うと開発者の生産性が向上します。 ソリューションの起動と読み込み、テスト検出、入力待機時間のパフォーマンスと信頼性が向上しました。 よりよいコードをより早く作成するのに役立つ機能も追加および強化されました。 たとえば、逆コンパイルされたアセンブリへの移動、入力時の変数名の提案、テスト エクスプローラーの階層ビュー、ファイル/型/メンバー/シンボルの宣言に移動するための [すべてに移動] (**Ctrl + T**)、インテリジェントな例外ヘルパー、コード スタイルの構成と適用、多くのリファクタリングとコード修正などがあります。 

このガイドに従って、生産性を最適化してください。

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>別の拡張機能/エディター/IDE のキーボード ショートカットを使用しています。

別の IDE またはコーディング環境から切り替えた場合は、以下のいずれかの拡張機能をインストールすると役立つ場合があります。

- [Emacs エミュレーション](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Visual Studio のホット キー (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

よく使用される Visual Studio のショートカットを以下に示します。 

> [!NOTE]
> 一部の拡張機能では既定の Visual Studio キー バインドが解除されるため、以下のコマンドを使用するにはキー バインドを復元する必要があります。 キー バインドを Visual Studio の既定値に復元するには、**[ツール] > [設定のインポートとエクスポート] > [すべての設定をリセット]** または **[ツール] > [オプション] > [キーボード] > [リセット]** を使います。

| ショートカット (すべてのプロファイル) | コマンド | 説明 |
|-|-|-|
| **Ctrl + T** | すべてにジャンプ | 任意のファイル、型、メンバー、またはシンボルの宣言に移動します |
| **F12** (**Ctrl キーを押しながらクリック**でも可能) | [定義へ移動] | シンボルが定義されている場所に移動します |
| **Ctrl + F12** | 実装に移動 | 基本データ型またはメンバーから、さまざまな実装に移動します |
| **Shift+F12** | [すべての参照の検索] | すべてのシンボルまたはリテラルの参照を表示します |
| **Ctrl**+**.** (C# Profile では **Alt + Enter** でも可能) | クイック アクションとリファクタリング | そのカーソル位置またはコード選択で、どのコード修正、コード生成アクション、リファクタリング、その他クイック アクションが使用できるかを表示します |
| **Ctrl** + **D** | 行の複製 | カーソルのあるコード行を複製します (**Visual Studio 2017 バージョン 15.6** 以降で使用可能) |
| **Shift** + **Alt** + **+**/**-** | 選択範囲の拡大/縮小 | エディターの現在の選択範囲を拡大または縮小します (**Visual Studio 2017 バージョン 15.5** 以降で使用できます) |
| **Ctrl + Q** | クイック起動 | すべての Visual Studio の設定を検索します |
| **F5** | デバッグの開始 | アプリケーションのデバッグを開始します |
| **Ctrl + F5** | デバッグなしで開始 | デバッグなしでアプリケーションをローカルで実行します |
| **Ctrl + K、D** (既定のプロファイル) または **Ctrl + E、D** (C# Profile) | ドキュメントのフォーマット | 改行文字、間隔、およびインデント設定に基づき、ファイルの書式設定の違反をクリーンアップします |
| **Ctrl + \\、E** (既定のプロファイル) または **Ctrl + W、E** (C# Profile) | エラー一覧の表示 | ドキュメント、プロジェクト、またはソリューション内のすべてのエラーを表示します |

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>ファイルまたは型にすばやく移動する方法が必要です。
Visual Studio 2017 には、"_すべてに移動_" という機能があります (**Ctrl + T**)。 [すべてに移動] を使うと、ファイル、型、メンバー、またはシンボルの宣言にすばやく移動できます。
- **歯車**アイコンで、この検索バーの場所を変更したり、"ライブ ナビゲーション プレビュー" をオフにしたりします
- クエリ構文 (例: "t mytype") を使って結果をフィルター処理します。 検索の範囲を現在のドキュメントだけにすることもできます。
- キャメル ケースの一致がサポートされています。

![Visual Studio の [すべてに移動]](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide-go-to-all")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>チームにはコードベースに適用されるコード スタイル ルールがあります。
.editorconfig ファイルを使って、コーディング規則を体系化できます。 .editorconfig ファイルの追加および編集用に、[EditorConfig 言語サービス拡張機能](https://aka.ms/editorconfig)をインストールすることをお勧めします。 すべて .NET コーディング規則オプションに関する[ドキュメント](https://aka.ms/editorconfigDocs)を確認することをお勧めします。

.editorconfig の例については[こちら](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8)をご覧ください。

![Visual Studio でのコード スタイルの適用](../ide/media/VS2017Guide-code-style.png "VS2017Guide-code-style")

### <a name="i-need-more-refactorings-and-code-fixes"></a>さらに多くのリファクタリングとコード修正が必要です。
Visual Studio 2017 には、多くのリファクタリング、コード生成アクション、コード修正が含まれます。詳しくは、[ドキュメント](https://aka.ms/refactorings)をご覧ください。 赤の波線はエラー、緑の波線は警告、3 つのグレーの点はコード提案をそれぞれ表します。

電球/ドライバーのアイコンをクリックするか、**Ctrl + .**  または **Alt + Enter** キーを押すことによって、コード修正にアクセスできます。 各修正にはプレビュー ウィンドウが付属しており、修正の効果によるライブ コードの相違が示されます。

よく使われる簡易修正とリファクタリングとしては、名前の変更、メソッドの抽出、メソッド シグネチャの変更、コンストラクターの生成、メソッドの生成、ファイルへの型の移動、Null チェックの追加、パラメーターの追加、不要な using の削除などがあります。

リファクタリングとコードの修正は、[Roslyn アナライザー](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix)で簡単に記述できます。 何人かのコミュニティ メンバーが、コードの検査を追加する "*無料*" の拡張機能を作成しています (Visual Studio の Roslynator と SonarLint)。 

![Visual Studio でのリファクタリング](../ide/media/VS2017Guide-refactoring.png "VS2017Guide-refactoring")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>使用状況の検索、実装への移動、逆コンパイルされたアセンブリへの移動が必要です
Visual Studio 2017 には、コードベースの検索とナビゲーションに役立つ多くの機能があります。たとえば、[すべての参照の検索] (**Shift + F12** キー)、[実装に移動] (**Ctrl + F12** キー)、[定義へ移動] (**F12** キーまたは **Ctrl キーを押しながらクリック**) などです。 逆コンパイルされたアセンブリへのナビゲーションは、バージョン 15.6 で追加されました。 この機能を有効にするには、**[ツール] > [オプション] > [テキスト エディター] > [C#] > [詳細設定] > [逆コンパイルされたソースへのナビゲーションを有効にする]** の順に移動します。

![Visual Studio での逆コンパイルされたソースへのナビゲーション](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide-navigate-to-source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>単体テストを実行して確認する必要があります。
Visual Studio 2017 には、テスト エクスプローラーと _Live Unit Testing_ という 2 つの単体テスト用ツールがあります。 バージョン 15.6 では、テスト エクスプローラーのテスト検出の速度が大幅に向上しました。 また、階層並べ替えに対応するように UI のデザインが変更されています。

Visual Studio には、[Live Unit Testing](/test/live-unit-testing) と呼ばれる単体テスト機能もあります。 Live Unit Testing はバックグラウンドで継続的に動作し、コードの変更によって影響を受けたテストを実行して、テストの状態を通知するインライン エディターのアイコンを更新します。

![Visual Studio のテスト エクスプローラーでの階層ビュー](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hiearchy-test-explorer")

### <a name="what-other-features-do-i-need-to-know-about"></a>他にどのような機能について知っておく必要がありますか?
コードをいっそう効率的に記述できるようになるエディターと生産性の機能の一覧を次に示します。 一部の機能は、既定ではオフになっているので、有効にする必要があります (これらの機能は、お使いのコンピューターではインデックス項目、検討中、または現在実験段階である場合があります)。
- "*ソリューション エクスプローラーでのファイルの検索*" は、ソリューション エクスプローラーで作業中のファイルを強調表示します。
  - **[ツール] > [オプション] > [プロジェクトとソリューション] > [アクティブな項目をソリューション エクスプローラーで選択された状態にする]**
- "*参照アセンブリおよび NuGet パッケージでの型に対する using の追加*" は、参照されていない型の NuGet パッケージをインストールするためのコード修正に電球を表示します。
  - **[ツール] > [オプション] > [テキスト エディター] > [C#] > [詳細設定] > [参照アセンブリの型に using を提案する]** および **[NuGet パッケージの型に using を提案する]**
- "*完全なソリューション分析を有効にする*" と、[エラー一覧] にソリューション内のすべてのエラーが表示されます。
  - **[ツール] > [オプション] > [テキスト エディター] > [C#] > [詳細設定] > [完全ソリューション解析を有効にする]**
- "*逆コンパイルされたソースへのナビゲーションを有効にする*" と、外部ソースからの型/メンバーの [定義に移動] できるようになり、ILSpy 逆コンパイラを使ってメソッド本体を表示できます。
  - **[ツール] > [オプション] > [テキスト エディター] > [C#] > [詳細設定] > [逆コンパイルされたソースへのナビゲーションを有効にする]**
- IntelliSense の "*入力候補/提案モード*" は、入力候補の動作を変更します。 IntelliJ の知識がある開発者は、この既定動作を変更することがよくあります。
  - **[メニュー] > [編集] > [IntelliSense] > [完了モードの切り替え]**
- 一般的なスケルトンをスタブ化するのに役立つ "*コード スニペット*" があります (Tab キーを 1 回押します)。 [完全な一覧](/ide/visual-csharp-code-snippets)をご覧ください。

![Visual Studio のコード スニペット](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide-code-snippet")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>生産性向上機能が見つからない、またはパフォーマンスが低下している場合
複数の方法でフィードバックを送ることができます。
- .NET 機能要求は [GitHub リポジトリ](https://github.com/dotnet/roslyn/issues)で提出できます。
- Visual Studio の機能要求、バグ、パフォーマンスの問題は、Visual Studio ウィンドウの上部にある **[フィードバックの送信]** アイコンで提出できます。


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> .NET 開発者向けの Visual Studio 2017 の概要

### <a name="smart-code-editor"></a>スマート コード エディター

- [ドキュメント: IntelliSense の使用](using-intellisense.md)
- [ドキュメント: スマート エディターの機能](writing-code-in-the-code-and-text-editor.md)

Visual Studio は .NET ("Roslyn") コンパイラを使ってコードの内容を深く理解します。これにより、構文の色付け、コード補完、誤入力された変数のスペルチェック、インポートされていない型の解決、アウトライン、構造ビジュアライザ、[CodeLens](find-code-changes-and-other-history-with-codelens.md)、呼び出し階層、ホバーが可能なクイック インフォ、パラメーターのヘルプなどのスマート編集機能だけでなく、リファクタリング、クイック アクションの適用、コードの生成のためのツールも提供されます。

![Visual Studio スマート コード エディター](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>コードベース内の移動と検索

[ドキュメント: コード内の移動](navigating-code.md)

*[すべてにジャンプ]* ショートカット (**Ctrl + T**) でファイル、型、メンバー、シンボルの宣言にジャンプすることで、.NET コードをすばやく移動できます。 .NET 言語間の参照を含め、コードのシンボルまたはリテラルのすべての参照を検索します (**Shift+F12**)。 さらに、対象が設定されているナビゲーション コマンドを使用すると、シンボルの定義 (**F12**) または実装 (**Ctrl + F12**) に直接ジャンプできます。

![[すべてにジャンプ] および [すべての参照の検索]](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>コード品質のライブ コード分析

[ドキュメント: リファクタリングとクイック アクション](refactoring-code-generation-quick-actions.md)

Visual Studio には、エラーと問題を起こす可能性のあるコードを検出することでコード品質を高めるライブ コード診断の機能があります。 ドキュメント、プロジェクト、またはソリューション全体で検出された問題を解決するためのクイック アクション (**Ctrl** + **.**) が提供されています。 エディターでソリューション ファイル全体を開いていない場合でも問題を検索するには、*完全ソリューション解析*を有効にします。

さらに、**Ctrl** + **.** のショートカットではコード修正候補を使用してベスト プラクティス、スタブ、コードの生成、コードのリファクタリングについて理解したり、新しい言語の機能を採用したりすることができます。 ショートカットによりコーディング規則の構成が有効になり、コーディング スタイルの違反が検出され、スタイルの問題を修復するためのクイック修正が提供されます。

![電球メニューを使用してクイック修正とリファクタリングを適用する](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>単体テスト

[ドキュメント: Visual Studio での単体テスト](../test/improve-code-quality.md)

.NET Framework、.NET Standard、.NET Core を対象とするすべてのアプリケーションに対し、MSTest、NUnit、または XUnit テストに基づく単体テストを実行してデバッグします。 *テスト エクスプローラー*でテストを探索して確認するか、*Live Unit Testing* (Enterprise SKU のみ) を使用してコードの変更が単体テストにどのように影響するかをエディター内ですぐに確認します。

![Visual Studio の Live Unit Testing](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>コードの整合性とスタイル

- [ドキュメント: 移植可能なカスタム エディター オプション](create-portable-custom-editor-options.md)
- [ドキュメント: .NET の EditorConfig コード スタイル設定](editorconfig-code-style-settings-reference.md)

Visual Studio では、**Ctrl** + **.** のショートカットによりコーディング規則の構成が有効になり、コーディング スタイルの違反が検出され、スタイルの問題を修復するためのクイック修正が提供されます。 ショートカットによりコーディング規則の構成が有効になり、コーディング スタイルの違反が検出され、スタイルの問題を修復するためのクイック修正が提供されます。 *EditorConfig* を使用して、リポジトリ間でのチームの書式設定、名前付け、コード スタイルの規則を構成して適用することで、プロジェクトとファイル レベルでの値のオーバーライドが可能になります。

![EditorConfig を使用してコーディング規則を構成して適用する](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>デバッグ

[ドキュメント: Visual Studio でのデバッグ](../debugger/index.md)

Visual Studio には、.NET Framework、.NET Standard、および .NET Core を対象とする .NET アプリケーションをデバッグできる優れたデバッガーが含まれています。 条件付きブレークポイントの切り替えと設定を行い (**F9**)、メソッド呼び出しにステップ インし、LINQ とラムダ式を評価し、変数ウォッチを設定し、プロセスに再接続し、コール スタックを調査するだけでなく、*エディット コンティニュ*でのデバッグ中にライブ コード編集も行うことができます。

サービスを Azure で実行している場合は、 *スナップショットのデバッグ*を使用して、Visual Studio 2017 Enterprise でリアルタイムに展開されているクラウド アプリケーションの問題を診断します。

![Visual Studio でのデバッグ](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>バージョン管理

[ドキュメント: Visual Studio でのバージョン管理](/vsts/index)

Git または TFVC を使用して Visual Studio でコードを格納して更新します。 エディター内でチーム エクスプローラーを使用してローカルの変更を整理し、ステータス バーで保留中のコミットと変更を追跡します。 [Continuous Delivery Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) 拡張機能を使用して Visual Studio 内の継続的インテグレーションと配信を設定し、アジャイル開発者のワークフローを採用します。

![Visual Studio のソース管理](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>機能拡張

[ドキュメント: Visual Studio の拡張](../extensibility/index.md)

Visual Studio には必要に応じたインストールや作成が可能な拡張機能の豊富なエコシステムが含まれています。 *拡張機能ギャラリー*または *Visual Studio Marketplace* から拡張機能をインストールするか、*VS SDK* を使用して独自のエディター プラグインをビルドするか、*.NET コンパイラ プラットフォーム SDK* を使用して独自のライブ コード アナライザまたはリファクタリングを作成します。 [Microsoft Code Analysis](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 拡張機能をダウンロードすると、その他のコード修正と修正候補を見つけることができます。

![Visual Studio 拡張機能ギャラリー](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
