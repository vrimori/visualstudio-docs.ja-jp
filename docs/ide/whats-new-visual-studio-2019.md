---
title: Visual Studio 2019 Preview の新機能
titleSuffix: ''
description: Visual Studio 2019 のプレビュー リリースの新機能について説明します。
ms.date: 12/19/2018
ms.prod: visual-studio-dev16
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e387485d2a11867944e980a9bad26261fd4a707c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848549"
---
# <a name="what39s-new-in-visual-studio-2019-preview"></a>Visual Studio 2019 Preview の新機能

**[16.0 Preview 1 リリース](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)の更新**

Visual Studio 2019 Preview には、開発者の生産性とチーム コラボレーションを最適化する新機能と共に、多くの全般的な機能強化が含まれています。 今回初めて Visual Studio を使用する場合も、何年も使用している場合でも、開発ライフ サイクルのあらゆる面で (簡略化されたプロジェクトの作成とコードの正常性管理から、チームおよびオープン ソースのコラボレーション ワークフローまで) その機能を利用することができます。

Visual Studio が提供する機能の基本的な概要を次に示します。

* **[個人およびチームの生産性](#personal-and-team-productivity)**。 生産性が最も重要な場所のすべての人に対する生産性。
* **[最新の開発サポート](#modern-development-support)**。 現在のプロジェクトおよび将来のソリューションへのサポート。
* **[継続的なイノベーション](#continuous-innovation)**。 インテリジェントなクラウドを利用したサポートによるコード スマート。

> [!NOTE]
> Visual Studio 2019 Preview の新機能の一覧については、[リリース ノート](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)をご覧ください。

## <a name="personal-and-team-productivity"></a>個人およびチームの生産性

パフォーマンスの向上は当然ながら Visual Studio のすべてのリリースで最も重視されていますが、生産性の向上も同じくらい重視されています。 それをどのように支援しているかについて説明します。

### <a name="new-start-window"></a>新しいスタート ウィンドウ

Visual Studio 2019 を開いてまず気付くことは、新しいスタート ウィンドウです。

   ![Visual Studio 2019 の新しいスタート ウィンドウ](../ide/media/start-window.png)

この新しい新しいスタート ウィンドウには、コードの複製またはチェックアウト、プロジェクトまたはソリューションを開く、ローカル フォルダーを開く、または新しいプロジェクトを作成するためのオプションが表示されます。 これらのオプションを単純なダイアログに表示することで、Visual Studio を初めて使うユーザーも上級ユーザーもすばやくコードに到達することができます。

詳しくは、「[Get to code:How we designed the new Visual Studio start window (コードを取得: 新しい Visual Studio 開始ウィンドウの設計方法)](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/)」のブログ投稿をご覧ください。

### <a name="better-search"></a>検索の向上

新しい検索エクスペリエンス (以前のクイック起動) は、より高速でより効果的になりました。 入力すると、検索結果が動的に表示されるようになりました。 また、将来使用するためにコマンドをより簡単に記憶できるように、検索結果にコマンドのキーボード ショートカットが含まれるようになりました。

   ![Visual Studio 2019 の新しい検索機能](../ide/media/search-feature.png)

新しい検索機能は、探しているものがコマンド、設定、ドキュメント、またはその他の便利な機能であるかに関わらず、検索対象を見つけやすくします。

### <a name="one-click-code-cleanup"></a>ワンクリックのコード クリーンアップ

新しいドキュメントの正常性インジケーターと組み合わされたのが、新しいコード クリーンアップ コマンドです。 この新しいコマンドを使用して、警告と提案を特定し、ボタンをクリックして両方を修正することができます。

   ![Visual Studio 2019 の新しいコード クリーンアップ機能](../ide/media/code-cleanup.png)

クリーンアップにより、コードが書式設定され、[現在の設定](../ide/code-styles-and-quick-actions.md)、[.editorconfig files](../ide/create-portable-custom-editor-options.md)、または [Roslyn アナライザー](../code-quality/roslyn-analyzers-overview.md) のいずれかの提案に従って、任意のコード修正が適用されます。

### <a name="debugger-improvements"></a>デバッガーの強化

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>ウォッチ ウィンドウ内で検索し、ウォッチ値を書式設定する

以前にも使ったことがあるかもしれませんが、値セットの中の文字列をウォッチ ウィンドウで調べます。 Visual Studio 2019 Preview では、検索するオブジェクトと値を見つけやすくするため、ウォッチ、ローカル、自動変数のウィンドウに検索が追加されました。

また、ウォッチ、ローカル、自動変数のウィンドウに表示される値を書式設定することもできます。  任意のウィンドウ内でいずれかの項目をダブルクリックしてコンマ (",") を追加し、使用可能な書式指定子のドロップダウン リストにアクセスします。各書式指定子には、意図した効果の説明が含まれています。

   ![Visual Studio 2019 の新しいウォッチ ウィンドウと値の書式設定機能](../ide/media/search-watch-window.png)

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) は、コードベースとそのコンテキストをチームメイトと共有し、Visual Studio 内で直接、双方向のインスタント コラボレーションができるようにする開発者サービスです。 Live Share では自分が共有したプロジェクトをチームメイトがシームレスかつ安全に読み取り、移動、編集、デバッグすることができます。

また、Visual Studio 2019 Preview では、このサービスは既定でインストールされます。

詳しくは、「[Visual Studio Live Share for real-time code reviews and interactive education (Visual Studio Live Share のリアルタイム コード レビューと対話型の教育)](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/)」のブログ投稿をご覧ください。

## <a name="modern-development-support"></a>最新の開発サポート

### <a name="manage-pull-requests-prs-from-the-ide"></a>IDE からのプル要求 (PR) の管理

ダウンロードして Visual Studio 2019 Preview で使用できる新しい拡張機能を導入しました。 この新しい拡張機能を使用すると、Visual Studio IDE [(統合開発環境)](../get-started/visual-studio-ide.md) を離れることなく、チームからのプル要求を確認、実行、さらにはデバッグすることもできます。 現在、コードは Azure Repos でサポートされていますが、GitHub までサポートを拡大しており、全体的なエクスペリエンスを向上します。

今すぐ作業を開始するには、[Visual Studio 用のプル要求](https://aka.ms/pr4vs)拡張機能を Visual Studio Marketplace からダウンロードします。

### <a name="develop-with-net-core-3-preview-1"></a>.NET Core 3 Preview 1 を使用した開発

Visual Studio 2019 のプレビュー リリースでは、任意のプラットフォーム向けの [.NET Core 3](http://aka.ms/netcore3preview1) アプリケーションのビルドをサポートしています。 クロスプラット フォーム C++ 開発と、iOS や Xamarin を使った Android 向けの .NET モバイル開発のサポートと改善は引き続き行います。

   ![Visual Studio 2019 で .NET Core 3 Preview 1 を使用してアプリを開発する](../ide/media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>継続的なイノベーション

### <a name="per-monitor-aware-pma-rendering"></a>Per-monitor aware (PMA) レンダリング

異なる表示倍率で構成されているモニターを使用する場合、またはご使用のメイン デバイスとは異なる表示倍率を持つマシンにリモートで接続する場合、Visual Studio がぼやけて見えたり、間違ったスケールでレンダリングされる場合があります。

Visual Studio 2019 Preview 1 のリリースにより、Visual Studio を Per-monitor aware (PMA) アプリケーションにする一歩を踏み出しました。 使用している表示倍率に関係なく、Visual Studio が正しくレンダリングできるようにする基礎的な作業を行っています。

   ![Visual Studio 2019 の Per-monitor aware (PMA) レンダリング](../ide/media/per-monitor-aware-dpi-scaling.png)

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) は、人工知能 (AI) を使用したソフトウェア開発作業を強化するための拡張機能です。 IntelliCode は GitHub 上の 2,000 のオープン ソース プロジェクト (それぞれに 100 個以上の星が付いています) 全体をトレーニングして、レコメンデーションを生成します。

Visual Studio IntelliCode が生産性の強化に役立つ方法を次にいくつか示します。

* 文脈に合わせてコードの入力候補を示す
* チームのパターンやスタイルに準拠するように開発者を導く
* 見つけにくいコード問題を見つける
* コード レビューの焦点を本当に重要な領域に向ける

Visual Studio 向けの IntelliCode を初めてプレビューしたときには、C# しかサポートしていませんでした。 今回、Visual Studio で C++ のサポートに加え、XAML のサポートも追加されました。

C# を使用している場合は、独自のコードでカスタム モデルをトレーニングする機能も追加されました。

最新の更新プログラムについて詳しくは、「[Visual Studio IntelliCode supports more languages and learns from your code (Visual Studio IntelliCode はより多くの言語をサポートし、コードから学習する)](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/)」のブログ投稿をご覧ください。 また、拡張機能の詳細とダウンロード方法については、Microsoft DevLabs で「[Visual Studio IntelliCode - Preview (Visual Studio IntelliCode - プレビュー)](https://go.microsoft.com/fwlink/?linkid=872707)」をご覧ください。

## <a name="give-us-feedback"></a>フィードバックの送信

Visual Studio チームにフィードバックを送ることにどんな意味があるのでしょうか? お客様からのフィードバックは、すべて真剣に考慮することにしています。 フィードバックによって今後の動向が左右されることになります。

* Visual Studio を向上させることができるご提案がある場合は、[[提案の送信]](../ide/talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) ツールを使用して、ご提案を送信してください。

* ハング、クラッシュ、またはその他のパフォーマンスの問題が発生した場合、[[問題の報告]](../ide/talk-to-us.md#i-want-to-report-a-problem-with-visual-studio) ツールを使用すると、再現コードやサポート ファイルを簡単に Microsoft と共有することができます。

## <a name="see-also"></a>関連項目

* [Visual Studio 2019 リリース ノート](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect(); 2018 カンファレンス](https://www.microsoft.com/connectevent)
* [Visual Studio 2017 の新機能](whats-new-in-visual-studio.md)
