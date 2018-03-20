---
title: ".NET 開発者向けの Visual Studio 2017 | Microsoft Docs"
description: ".NET コードをより速く記述するための Visual Studio 2017 の機能の概要。"
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
ms.openlocfilehash: be14af66f5aa5389e9e701eb79dc68ee733c6068
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>.NET 開発者向けの Visual Studio 2017

## <a name="smart-code-editor"></a>スマート コード エディター

- [ドキュメント: IntelliSense の使用](using-intellisense.md)
- [ドキュメント: スマート エディターの機能](writing-code-in-the-code-and-text-editor.md)

Visual Studio は .NET ("Roslyn") コンパイラを使ってコードの内容を深く理解します。これにより、構文の色付け、コード補完、誤入力された変数のスペルチェック、インポートされていない型の解決、アウトライン、構造ビジュアライザ、[CodeLens](find-code-changes-and-other-history-with-codelens.md)、呼び出し階層、ホバーが可能なクイック インフォ、パラメーターのヘルプなどのスマート編集機能だけでなく、リファクタリング、クイック アクションの適用、コードの生成のためのツールも提供されます。

![Visual Studio スマート コード エディター](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>コードベース内の移動と検索

[ドキュメント: コード内の移動](navigating-code.md)

*[すべてにジャンプ]* ショートカット (**Ctrl + T**) でファイル、型、メンバー、シンボルの宣言にジャンプすることで、.NET コードをすばやく移動できます。 .NET 言語間の参照を含め、コードのシンボルまたはリテラルのすべての参照を検索します (**Shift+F12**)。 さらに、対象が設定されているナビゲーション コマンドを使用すると、シンボルの定義 (**F12**) または実装 (**Ctrl + F12**) に直接ジャンプできます。

![[すべてにジャンプ] および [すべての参照の検索]](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>コード品質のライブ コード分析

[ドキュメント: リファクタリングとクイック アクション](refactoring-code-generation-quick-actions.md)

Visual Studio には、エラーと問題を起こす可能性のあるコードを検出することでコード品質を高めるライブ コード診断の機能があります。 ドキュメント、プロジェクト、またはソリューション全体で検出された問題を解決するためのクイック アクション (**Ctrl** + **.**) が提供されています。 エディターでソリューション ファイル全体を開いていない場合でも問題を検索するには、*完全ソリューション解析*を有効にします。

さらに、**Ctrl** + **.** のショートカットではコード修正候補を使用してベスト プラクティス、スタブ、コードの生成、コードのリファクタリングについて理解したり、新しい言語の機能を採用したりすることができます。 ショートカットによりコーディング規則の構成が有効になり、コーディング スタイルの違反が検出され、スタイルの問題を修復するためのクイック修正が提供されます。

![電球メニューを使用してクイック修正とリファクタリングを適用する](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>単体テスト

[ドキュメント: Visual Studio での単体テスト](../test/improve-code-quality.md)

.NET Framework、.NET Standard、.NET Core を対象とするすべてのアプリケーションに対し、MSTest、NUnit、または XUnit テストに基づく単体テストを実行してデバッグします。 *テスト エクスプローラー*でテストを探索して確認するか、*Live Unit Testing* (Enterprise SKU のみ) を使用してコードの変更が単体テストにどのように影響するかをエディター内ですぐに確認します。

![Visual Studio の Live Unit Testing](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>コードの整合性とスタイル

- [ドキュメント: 移植可能なカスタム エディター オプション](create-portable-custom-editor-options.md)
- [ドキュメント: .NET の EditorConfig コード スタイル設定](editorconfig-code-style-settings-reference.md)

Visual Studio では、**Ctrl** + **.** のショートカットによりコーディング規則の構成が有効になり、コーディング スタイルの違反が検出され、スタイルの問題を修復するためのクイック修正が提供されます。 ショートカットによりコーディング規則の構成が有効になり、コーディング スタイルの違反が検出され、スタイルの問題を修復するためのクイック修正が提供されます。 *EditorConfig* を使用して、リポジトリ間でのチームの書式設定、名前付け、コード スタイルの規則を構成して適用することで、プロジェクトとファイル レベルでの値のオーバーライドが可能になります。

![EditorConfig を使用してコーディング規則を構成して適用する](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>デバッグ

[ドキュメント: Visual Studio でのデバッグ](../debugger/index.md)

Visual Studio には、.NET Framework、.NET Standard、および .NET Core を対象とする .NET アプリケーションをデバッグできる優れたデバッガーが含まれています。 条件付きブレークポイントの切り替えと設定を行い (**F9**)、メソッド呼び出しにステップ インし、LINQ とラムダ式を評価し、変数ウォッチを設定し、プロセスに再接続し、コール スタックを調査するだけでなく、*エディット コンティニュ*でのデバッグ中にライブ コード編集も行うことができます。

サービスを Azure で実行している場合は、 *スナップショットのデバッグ*を使用して、Visual Studio 2017 Enterprise でリアルタイムに展開されているクラウド アプリケーションの問題を診断します。

![Visual Studio でのデバッグ](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>バージョン管理

[ドキュメント: Visual Studio でのバージョン管理](/vsts/index)

Git または TFVC を使用して Visual Studio でコードを格納して更新します。 エディター内でチーム エクスプローラーを使用してローカルの変更を整理し、ステータス バーで保留中のコミットと変更を追跡します。 [Continuous Delivery Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) 拡張機能を使用して Visual Studio 内の継続的インテグレーションと配信を設定し、アジャイル開発者のワークフローを採用します。

![Visual Studio のソース管理](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>機能拡張

[ドキュメント: Visual Studio の拡張](../extensibility/index.md)

Visual Studio には必要に応じたインストールや作成が可能な拡張機能の豊富なエコシステムが含まれています。 *拡張機能ギャラリー*または *Visual Studio Marketplace* から拡張機能をインストールするか、*VS SDK* を使用して独自のエディター プラグインをビルドするか、*.NET コンパイラ プラットフォーム SDK* を使用して独自のライブ コード アナライザまたはリファクタリングを作成します。 [Microsoft Code Analysis](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 拡張機能をダウンロードすると、その他のコード修正と修正候補を見つけることができます。

![Visual Studio 拡張機能ギャラリー](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>よく使用されている拡張機能とショートカット

別の IDE またはコーディング環境から切り替えた場合は、以下のいずれかの拡張機能をインストールすると役立つ場合があります。

- [Emacs エミュレーション](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [Visual Studio のホット キー (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

よく使用される Visual Studio のショートカットを以下に示します。 一部の拡張機能では既定の Visual Studio キー バインドが解除されるため、以下のコマンドを使用するためにキー バインドを復元する必要があることに注意してください。 キー バインドを Visual Studio の既定値に復元するには、**[ツール]、[設定のインポートとエクスポート]、[すべての設定をリセット]** の順に移動します。

| ショートカット (すべてのプロファイル) | コマンド | 説明 |
|-|-|-|
| **Ctrl + T** | すべてにジャンプ | 任意のファイル、型、メンバー、またはシンボルの宣言に移動します |
| **F12** (**Ctrl キーを押しながらクリック**でも可能) | [定義へ移動] | シンボルが定義されている場所に移動します |
| **Ctrl + F12** | 実装に移動 | 基本データ型またはメンバーから、さまざまな実装に移動します |
| **Shift+F12** | [すべての参照の検索] | すべてのシンボルまたはリテラルの参照を表示します |
| **Ctrl**+**.** (C# Profile では **Alt + Enter** でも可能) | クイック アクションとリファクタリング | そのカーソル位置またはコード選択で、どのコード修正、コード生成アクション、リファクタリング、その他クイック アクションが使用できるかを表示します |
| **Ctrl** + **E**、**V** | 行の複製 | カーソルのあるコード行を複製します (**Visual Studio 2017 バージョン 15.6** 以降で使用可能) |
| **Ctrl + Q** | クイック起動 | すべての Visual Studio の設定を検索します |
| **F5** | デバッグの開始 | アプリケーションのデバッグを開始します |
| **Ctrl + F5** | デバッグなしで開始 | デバッグなしでアプリケーションをローカルで実行します |
| **Ctrl + K、D** (既定のプロファイル) または **Ctrl + E、D** (C# Profile) | ドキュメントのフォーマット | 改行文字、間隔、およびインデント設定に基づき、ファイルの書式設定の違反をクリーンアップします |
| **Ctrl + \\、E** (既定のプロファイル) または **Ctrl + W、E** (C# Profile) | エラー一覧の表示 | ドキュメント、プロジェクト、またはソリューション内のすべてのエラーを表示します |