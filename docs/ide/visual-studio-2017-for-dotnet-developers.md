---
title: .NET 開発の生産性を向上させる
description: より良い .NET コードをより早く書き込むのに役立つ、移動、コード分析、単体テスト、およびその他の機能の概要。
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: ef9101a0dbad68dd75792f34526bac550a331286
ms.sourcegitcommit: a6734c4d76dae3d21b55b10f3bc618dfa6b62dea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "42626826"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Visual Studio 2017 C# の生産性ガイド

[Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) によって開発者の生産性がどのように向上するかを説明します。 逆コンパイルされたアセンブリへの移動、入力時の変数名の提案、**テスト エクスプローラー**の階層ビュー、ファイル/型/メンバー/シンボルの宣言に移動するための [すべてに移動] (**Ctrl** + **T**)、インテリジェントな**例外ヘルパー**、コード スタイルの構成と適用、多くのリファクタリングとコード修正など、パフォーマンスと生産性を向上させる機能を利用できます。

## <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>別の拡張機能/エディター/IDE のキーボード ショートカットを使い慣れています

**Visual Studio 2017 バージョン 15.8 の新機能** 別の IDE やコーディング環境から切り替えた場合は、キーボード スキームを *Visual Studio Code* または *ReSharper (Visual Studio)* に変更することができます。

![Visual Studio のキーボード スキーム](../ide/media/VS2017Guide-Keyboard.png)

次の一部の拡張機能でも、キーボード スキームが提供されます。

- [Visual Studio のホット キー (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs エミュレーション](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

よく使用される Visual Studio のショートカットを以下に示します。

| ショートカット (すべてのプロファイル) | コマンド | 説明 |
|-|-|-|
| **Ctrl** + **T** | すべてにジャンプ | 任意のファイル、型、メンバー、またはシンボルの宣言に移動します |
| **F12** (**Ctrl** を押しながら**クリック**でも可能) | [定義へ移動] | シンボルが定義されている場所に移動します |
| **Ctrl** + **F12** | 実装に移動 | 基本データ型またはメンバーから、さまざまな実装に移動します |
| **Shift** + **F12** | [すべての参照の検索] | すべてのシンボルまたはリテラルの参照を表示します |
| **Ctrl**+**.** (C# Profile では **Alt** + **Enter** でも可能) | クイック アクションとリファクタリング | そのカーソル位置またはコード選択で、どのコード修正、コード生成アクション、リファクタリング、その他クイック アクションが使用できるかを表示します |
| **Ctrl** + **D** | 行の複製 | カーソルのあるコード行を複製します (**Visual Studio 2017 バージョン 15.6** 以降で使用可能) |
| **Shift** + **Alt** + **+**/**-** | 選択範囲の拡大/縮小 | エディターの現在の選択範囲を拡大または縮小します (**Visual Studio 2017 バージョン 15.5** 以降で使用できます) |
| **Ctrl**  +  **Alt**  +  **.** | 次の一致にキャレットを挿入 | 現在の選択範囲と一致する次の場所で選択内容とキャレットを追加します (**Visual Studio 2017 バージョン 15.8** 以降で利用可能)。 |
| **Ctrl** + **Q** | クイック起動 | すべての Visual Studio の設定を検索します |
| **F5** | デバッグの開始 | アプリケーションのデバッグを開始します |
| **Ctrl** + **F5** | デバッグなしで開始 | デバッグなしでアプリケーションをローカルで実行します |
| **Ctrl** + **K**、**D** (既定のプロファイル) または **Ctrl** + **E**、**D** (C# Profile) | [ドキュメントのフォーマット](code-styles-and-quick-actions.md#format-document-command) | 改行文字、間隔、およびインデント設定に基づき、ファイルの書式設定の違反をクリーンアップします |
| **Ctrl** + **\\**、**Ctrl** + **E** (既定のプロファイル) または **Ctrl** + **W**、**E** (C# Profile) | エラー一覧の表示 | ドキュメント、プロジェクト、またはソリューション内のすべてのエラーを表示します |
| **Alt**  +  **PgUp/PgDn** | 次/前の問題に移動 | ドキュメント内の前/次のエラー、警告、提案に移動します (**Visual Studio 2017 バージョン 15.8** 以降で利用可能)。 |

> [!NOTE]
> 一部の拡張機能によって、既定の Visual Studio キー バインドがバインド解除されます。 上記のコマンドを使用するには、**[ツール]** > **[設定のインポートとエクスポート]** > **[すべての設定をリセット]** または **[ツール]** > **[オプション]** > **[キーボード]** > **[リセット]** の順に進み、キー バインドを Visual Studio の既定値に復元します。

Visual studio のキーボード ショートカットとコマンドの詳細については、[こちらのドキュメント](..\ide\tips-and-tricks-for-visual-studio.md)を参照してください。

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>ファイルまたは型にすばやく移動する方法が必要です

Visual Studio 2017 には、"**すべてに移動**" という機能があります (**Ctrl** + **T**)。 **[すべてに移動]** を使うと、ファイル、型、メンバー、またはシンボルの宣言にすばやく移動できます。

- **歯車**アイコンで、この検索バーの場所を変更したり、"ライブ ナビゲーション プレビュー" をオフにしたりします。
- クエリ構文 (例: "t mytype") を使って結果をフィルター処理します。 検索の範囲を現在のドキュメントだけにすることもできます。
- キャメル ケースの一致がサポートされています。

![Visual Studio の [すべてに移動]](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>チームにはコードベースに適用されるコード スタイル ルールがあります

*.editorconfig* ファイルを使って、コーディング規則を体系化し、ソースとともに移動させることができます。

- Visual Studio の *.editorconfig* ファイルの追加と編集が簡単になる、[EditorConfig 言語サービス拡張機能](https://aka.ms/editorconfig)をインストールできます。
- [Visual Studio の IntelliCode 拡張機能](/visualstudio/intellicode/intellicode-visual-studio)をお試しください。 この実験的な拡張機能では、ユーザーのコード スタイルが既存のコードから推測され、既に定義したコード スタイルの設定を使用して空でない *.editorconfig* ファイルが作成されます。
- .NET コーディング規則オプションに関する[ドキュメント](https://aka.ms/editorconfigDocs)を確認してください。
- *.editorconfig* ファイルの例については[こちら](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8)をご覧ください。

![Visual Studio でのコード スタイルの適用](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>さらなるリファクタリングとコード修正が必要です

Visual Studio 2017 には、多くのリファクタリング、コード生成アクション、コード修正が含まれます。 赤の波線はエラー、緑の波線は警告、3 つのグレーの点はコード提案をそれぞれ表します。 コード修正にアクセスするには、電球/ドライバーのアイコンをクリックするか、**Ctrl** + **.** キー または **Alt** + **Enter** キーを押します。 各修正にはプレビュー ウィンドウが付属しており、修正の効果によるライブ コードの相違が示されます。

- 一般的なクイック修正とリファクタリングには、次の内容が含まれます。
  - *名前の変更*
  - *メソッドの抽出*
  - *メソッド シグネチャの変更*
  - *コンストラクターの生成*
  - *メソッドの生成*
  - *ファイルへの型の移動*
  - *Null チェックの追加*
  - *パラメーターの追加*
  - *不要な using の削除*
  - [ドキュメント](https://aka.ms/refactorings)で詳細を確認してください
- 独自のリファクタリングまたはコード修正は [Roslyn アナライザー](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix)を使用して記述します。
- 何人かのコミュニティ メンバーが、コードの検査を追加する、次のような無料の拡張機能を作成しています。
  - [FXCop アナライザー](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Visual Studio でのリファクタリング](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>使用状況の検索、実装への移動、逆コンパイルされたアセンブリへの移動が必要です

Visual Studio 2017 には、コードベースの検索と移動に役立つ多くの機能があります。 [コード ナビゲーションの機能](../ide/navigating-code.md)の詳細を確認してください

| 機能 | ショートカット | 詳細/機能強化 |
|- | - | -|
| [すべての参照の検索] | **Shift** + **F12**| 結果はプロジェクト、定義などによって、色分け表示してグループ化できます。結果を 'ロックする' こともできます。 |
| 実装に移動 | **Ctrl** + **F12** | オーバーライドされたメンバーに移動するには、`override` キーワードの [定義へ移動] を使用します |
| [定義へ移動] | **F12** または **Ctrl** キーを押しながら**クリック**| **Ctrl** キーを押しながらクリックして定義へ移動することができます |
| 定義をここに表示 | **Alt** + **F12** | 定義のインライン ビュー |
| 構造ビジュアライザー | 中かっこの間の灰色の点線 | マウス ポインターを合わせると、コードの構造を参照できます |
| 逆コンパイルされたアセンブリへの移動 | **F12** または **Ctrl** キーを押しながら**クリック** | **[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[詳細設定]** > **[Enable navigation to decompiled sources]\(逆コンパイルされたソースへの移動を有効にする\)** で機能を有効にして、外部ソース (ILSpy によって逆コンパイル済み) に移動します。 |

![[すべてに移動] および [すべての参照の検索]](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>単体テストを実行して確認する必要があります

Visual Studio 2017 ではテストの操作性に多数の機能強化を行いました。 MSTest v1、MSTest v2、NUnit、XUnit のテスト フレームワークで単体テストの操作性をお試しください。

- **テスト エクスプローラー**のテスト検出はバージョン 15.6 で高速化しています (最適な結果を得るには、最新バージョンのテスト アダプターにアップグレードしてください)。
- バージョン 15.6 の新しい*階層的な並べ替え*を使用して、テスト エクスプローラーでテストを整理してください。
- [Live Unit Testing](../test/live-unit-testing.md) は、コードの変更によって影響を受けたテストを継続的に実行して、テストの状態を通知するインライン エディターのアイコンを更新します。 *Live Test セット*との間で特定のテストまたはテスト プロジェクトを含めたり、除外したりしてください。

![Visual Studio のテスト エクスプローラーの階層ビュー](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>コードをデバッグする必要があります

Visual Studio 2017 では新しいデバッグ機能が多数追加されました。

- *[Run to click]\(クリックして実行\)* では、コードの行の隣にマウス ポインターを移動し、表示された緑色の [再生] をクリックして、該当する行に達するまでプログラムを実行することができます。
- 新しい**例外ヘルパー**のダイアログの最上位には、NullReferenceException のどの変数が 'null' になるかといった特に重要な情報があります。
- [[Step Back]\(前に戻る\)](../debugger/how-to-use-intellitrace-step-back.md) のデバッグにより、前のブレークポイントまたは手順に戻り、過去の時点でのアプリケーションの状態を確認できるようになります。
- [[スナップショットのデバッグ]](/azure/application-insights/app-insights-snapshot-debugger) では、例外がスローされた (Azure にスローされる必要があります) 時点での、ライブ Web アプリケーションの状態を調査することができます。

![Visual Studio 2017 の新しい例外ヘルパー](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>自分のプロジェクトでバージョン管理を使用する必要があります

Git または TFVC を使用して Visual Studio でコードを格納して更新することができます。

- **チーム エクスプローラー**を使用してローカルの変更を整理し、ステータス バーで保留中のコミットと変更を追跡します。
- [Continuous Delivery Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) 拡張機能を使用して Visual Studio 内のプロジェクトの継続的インテグレーションと継続的デリバリーを設定し、アジャイル開発者のワークフローを採用します。

![Visual Studio におけるソース管理](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>他にどのような機能について知っておく必要がありますか?

コードをいっそう効率的に記述できるようになるエディターと生産性の機能の一覧を次に示します。 一部の機能は、既定ではオフになっているので、有効にする必要があります (これらの機能は、お使いのコンピューターではインデックス項目、検討中、または現在実験段階である場合があります)。

| 機能 | 説明 | 有効にする方法 |
|-|-|-|
| ソリューション エクスプローラーでファイルを探す | **ソリューション エクスプローラー**で作業中のファイルを強調表示する | **[ツール]** > **[オプション]** > **[プロジェクトとソリューション]** > **[アクティブな項目をソリューション エクスプローラーで選択された状態にする]** |
| 参照アセンブリと NuGet パッケージの型に using を追加する | 参照されていない型の NuGet パッケージをインストールするためのコード修正を含む電球を表示します | **[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[詳細設定]** > **[参照アセンブリの型に using を提案する]** および **[NuGet パッケージの型に using を提案する]** |
| 完全ソリューション解析を有効にする | **エラー一覧**にソリューション内のすべてのエラーを表示します | **[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[詳細設定]** > **[完全ソリューション解析を有効にする]** |
| 逆コンパイルされたソースへの移動を有効にする | 外部ソースからの型/メンバーの [定義に移動] が可能になり、ILSpy 逆コンパイラを使ってメソッド本体を表示できます | **[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[詳細設定]** > **[逆コンパイルされたソースへのナビゲーションを有効にする]** |
| 補完/提案モード | IntelliSense の補完動作が変更されました -- IntelliJ の知識がある開発者は、この既定動作を変更することがよくあります | **[メニュー]** > **[編集]** > **[IntelliSense]** > **[完了モードの切り替え]** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | コードの参照情報と変更履歴をエディターに表示します | **[ツール]** > **[オプション]** > **[テキスト エディター]** > **[すべての言語]** > **[CodeLens]** |
| [コード スニペット](../ide/visual-csharp-code-snippets.md) | 一般的な定型句をスタブできるようにします |  スニペットの名前を入力し、**Tab** キーを 2 回押します。 |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>生産性向上機能が見つからない、またはパフォーマンスが低下している場合

複数の方法でフィードバックを送ることができます。

- .NET 機能要求は [GitHub リポジトリ](https://github.com/dotnet/roslyn/issues)で提出できます。
- Visual Studio の機能要求、バグ、パフォーマンスの問題は、Visual Studio ウィンドウの右上にある **[フィードバックの送信]** アイコンで提出できます。
