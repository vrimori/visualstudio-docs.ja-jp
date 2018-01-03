---
title: "Visual Studio での Python |Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 8cd00fe33cf463227dd09f93047350a96cee3b92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-python-in-visual-studio"></a>Visual Studio での Python の使用

Python は、信頼性と柔軟性に優れ、簡単に学ぶことができ、すべてのオペレーティング システムで自由に使える一般的なプログラミング言語であり、強力な開発者コミュニティと多くの無料ライブラリによってサポートされています。 Python は、Web アプリケーション、Web サービス、デスクトップ アプリ、スクリプト、科学技術計算などのすべての開発方法をサポートし、多くの大学、科学者、一般の開発者、プロの開発者によって同様に使われています。 この言語について詳しくは、[python.org](https://www.python.org) および「[Python for Beginners](https://www.python.org/about/gettingstarted/)」(初心者向けの Python) をご覧ください。

Windows の Visual Studio では、Python の開発およびデータ サイエンス ワークロードによる Python 言語の[オープンソース](https://github.com/Microsoft/ptvs) サポート (Visual Studio 2017) および無料の Python Tools for Visual Studio 拡張機能 (Visual Studio 2015 以降) が提供されています。 現在、Python は Visual Studio for Mac ではサポートされていませんが、Visual Studio Code によって Mac と Linux でも使うことができます (後の「[質問と回答](#questions-and-answers)」を参照)。

開始するには:

- [インストール手順](installation.md)に従って、Python ワークロードを設定します。
- 1 つ以上のクイックスタートを使用して、プロジェクトを作成します。 わからない場合は、[テンプレートからプロジェクトを作成する](quickstart-02-project-from-template.md)のクイックスタートから始めます。
- 完全なエンド ツー エンドのエクスペリエンスの場合は、[Visual Studio での Python の使用](vs-tutorial-01-01.md)のチュートリアルに従います。
- 次に、以下のリンクを使って Python 関連の機能と Visual Studio 自体の機能について詳しく見てください。

| 機能 | 説明 | Visual Studio の一般的なドキュメント | 
| --- | --- | --- |
| [Visual Studio のプロジェクト システム](python-projects.md) | Python コードのフォルダー構造を暗黙的に取得し、アプリ コード、テスト コード、Web ページ、JavaScript、ビルド スクリプトなどの識別を明示的に制御できます。 | [Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md) |
| [プロジェクト テンプレート](python-projects.md#project-templates) | コンソール、Web、Azure、データ サイエンス、他の種類のプロジェクト用のプロジェクト構造を短時間で作成します。 | [Visual Studio テンプレート](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| 複数のインタープリターのサポート | さまざまなバージョンの CPython と IronPython をサポートします。 | N/A |
| IPython のサポート | インライン プロット、.NET、および Windows Presentation Foundation (WPF) のための REPL での IPython/Jupyter のサポートが含まれます。 | N/A |
| [豊富な編集、IntelliSense、コード読解](code-editing.md) | 構文の色分け、すべてのコードとライブラリ間でのオートコンプリート、[コードのフォーマット](code-formatting.md)、シグネチャ ヘルプ、クラス ビュー、定義への移動、すべての参照の検索、コード スニペット、[リファクタリング](code-refactoring.md)、[PyLint](code-pylint.md) などを含みます。 | [コード エディターとテキスト エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md) |
| [対話型ウィンドウ](interactive-repl.md) | コードの一部を簡単に強調表示してそれを対話型ウィンドウに送信する機能を備えた、Python 用のクイック REPL エクスペリエンスを提供します。 | N/A |
| [フル機能のデバッグ](debugging.md) | Visual Studio プロジェクトを使っても使わなくてもデバッグを行うことができ、既存の実行可能ファイルをデバッグする機能、[Python/C++ 混合モードのデバッグ](debugging-mixed-mode.md)、Windows/Linux/Mac への[リモート デバッグ](debugging-cross-platform-remote.md)、[Azure へのリモート デバッグ](debugging-azure-remote.md)、および対話型ウィンドウ内でのデバッグを含みます。 | [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md) |
| [包括的なレポートを備えたプロファイリング ツール](profiling.md) | アプリケーション内で時間がどのように費やされているかを調べます。異なるプロファイリング実行の間でパフォーマンスを比較する機能を含みます。 | [プロファイリング ツール](../profiling/profiling-tools.md)(Visual Studio のプロファイリング機能の一部は、Python では使用できません) |
| [単体テスト ツール](unit-testing.md) | Visual Studio テスト エクスプローラーでテストを検出、実行、および管理し、単体テストを簡単にデバッグします。 | [コードの単体テスト](../test/unit-test-your-code.md) |

Python ワークロードに含まれる [Azure SDK for Python](azure-sdk-for-python.md) を使うと、Windows、Mac OS X、Linux アプリから Azure サービスを簡単に利用できます。

概要のビデオについては、Microsoft Virtual Academy で短い「[Python Tools for Visual Studio](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)」 (Visual Studio の Python ツール) コース (合計で約 22 分) をご覧ください。 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]


## <a name="questions-and-answers"></a>質問と回答

**Q.Visual Studio for Mac では Python のサポートを利用できますか?**

A:  現時点では利用できませんが、[UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac) には要望が寄せられています。 [Visual Studio for Mac](https://docs.microsoft.com/visualstudio/mac/) のドキュメントでは、現在サポートされている開発の種類が示されています。 当面の間、Windows、Mac、Linux での Visual Studio Code は、[利用可能な拡張機能によって Python で問題なく動作します](https://code.visualstudio.com/docs/languages/python)。

**Q.Python で UI を構築するには何を使用できますか?**

A:  この分野の主なツールとして [Qt Project](https://www.qt.io/qt-for-application-development/) があり、[PySide (公式バインディング)](http://wiki.qt.io/PySide) ([PySide のダウンロード ページ](https://download.qt.io/official_releases/pyside/.)もご覧ください) や [PyQt](https://wiki.python.org/moin/PyQt) という Python のバインディングもあります。 現在のところ、Visual Studio の Python のサポートには、UI 開発用のツールは含まれていません。

**Q.Python プロジェクトでスタンドアロンの実行可能ファイルを作成できますか?**

A:  一般的に、Python はインタープリター言語であり、Visual Studio や Web サーバーなど、適切な Python 対応環境で、オンデマンドでコードが実行されます。 現在のところ、Python のスタンドアロンの実行可能ファイル (実質的には Python インタープリターが埋め込まれたプログラム) を作成する機能は Visual Studio にありません。 ただし、[StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)で説明されているように、Python コミュニティでは、実行可能ファイルを作成するさまざまな方法が紹介されています。 また、CPython はネイティブ アプリケーション内への埋め込みをサポートしています。詳細については、ブログの投稿「[Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/)」(CPython の埋め込み可能な Zip ファイルの使用方法) を参照してください。

## <a name="features-matrix"></a>機能一覧

[インストール ガイド](installation.md)の説明に従って、以下のエディションの Visual Studio に Python のサポートをインストールできます。

- [Visual Studio 2017 (全エディション)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (全エディション)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express for Web Update 2 以降
- Visual Studio 2013 Express for Desktop Update 2 以降
- Visual Studio 2013 (Pro エディション以上)
- Visual Studio 2012 (Pro エディション以上)
- Visual Studio 2010 SP1 (Pro エディション以上、.NET 4.5 が必要)

Visual Studio のバージョンおよびエディション別のサポートされる機能:

| Python のサポート | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 複数のインタープリターの管理 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 一般的なインタープリターの自動検出 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| カスタム インタープリターの追加 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 仮想環境 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pip/簡易インストール | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| プロジェクト システム | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 既存のコードから新しいプロジェクトを作成 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| すべてのファイルを表示 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| ソース管理 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Git 統合 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| 編集 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 構文の強調表示 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| オートコンプリート | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| シグネチャ ヘルプ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| クイック ヒント | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| オブジェクト ブラウザー/クラス ビュー | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| [ナビゲーション バー] | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 定義へ移動 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 移動 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| [すべての参照の検索] | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動インデント | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| コードのフォーマット | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| リファクタリング - 名前の変更 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| リファクタリング - メソッドの抽出 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| リファクタリング - インポートの追加と削除 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 対話型ウィンドウ | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 対話型ウィンドウ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| インライン グラフを含む IPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| デスクトップ | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| コンソール/Windows アプリケーション | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython WPF (XAML デザイナーを含む) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython Windows フォーム | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Django Web プロジェクト | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Bottle Web プロジェクト | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Flask Web プロジェクト | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| 汎用 Web プロジェクト | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Web サイトへの配置 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Web ロールへの配置 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| worker ロールへの配置 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Azure エミュレーターでの実行 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| リモート デバッグ | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| サーバー エクスプローラーのアタッチ | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Django テンプレート | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| デバッグ | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| オートコンプリート | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| CSS と JavaScript のオートコンプリート | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| デバッグ | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| デバッグ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| プロジェクトを使わないデバッグ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| デバッグ - 編集へのアタッチ | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 混合モードのデバッグ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| リモート デバッグ (Windows、Mac OS X、Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 対話型ウィンドウのデバッグ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| プロファイル | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| プロファイル | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| テスト | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| テスト エクスプローラー | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| テストの実行 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| テストのデバッグ | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. VS 2012 の Git サポートは、[Visual Studio ギャラリー](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c)で入手できる Visual Studio Tools for Git 拡張機能で利用可能です。

2. Azure Web サイトに配置するには、[Azure SDK for .NET 2.1 - VS 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855) が必要です。  以降のバージョンは VS 2010 をサポートしません。

3. Azure Web ロールおよびワーカー ロールのサポートには、[Azure SDK for .NET 2.3 - VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) 以降が必要です。

4. Azure Web ロールおよびワーカー ロールのサポートには、[Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

5. Visual Studio 2013 の Django テンプレート エディターには、Update 2 をインストールすることで解決される既知の問題がいくつかあります。

6. Windows 8 以降が必要です。 Visual Studio 2013 Express for Web には [プロセスにアタッチ] ダイアログがありませんが、Azure Web サイトのリモート デバッグはサーバー エクスプローラーの [デバッガーのアタッチ] (Python) コマンドを使って可能です。 リモート デバッグには、[Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

7. Windows 8 以降が必要です。 サーバー エクスプローラーの [デバッガーのアタッチ] (Python) コマンドには、[Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

8. Windows 8 以降が必要です。

## <a name="additional-resources"></a>その他の技術情報

- [PyKinect を使った Python での Kinect ゲームの作成](https://github.com/Microsoft/PTVS/wiki/PyKinect) (GitHub wiki)
- [IIS と Python の間の WFastCGI ブリッジ](https://pypi.python.org/pypi/wfastcgi) (python.org)
- [Microsoft Virtual Academy の無料 Python コース](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Python に関して寄せられることの多い質問 (Microsoft Virtual Academy)](https://aka.ms/mva-top-python-questions)
