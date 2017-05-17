---
title: "Visual Studio での Python |Microsoft Docs"
ms.custom: 
ms.date: 5/2/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: c46c8b7a0d9ea1509dcda2ef711562b3cf95b259
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---

# <a name="working-with-python-in-visual-studio"></a>Visual Studio での Python の使用

Python は、信頼性と柔軟性に優れ、簡単に学ぶことができ、すべてのオペレーティング システムで自由に使える一般的なプログラミング言語であり、強力な開発者コミュニティと多くの無料ライブラリによってサポートされています。 Python は、Web アプリケーション、Web サービス、デスクトップ アプリ、スクリプト、科学技術計算などのすべての開発方法をサポートし、多くの大学、科学者、一般の開発者、プロの開発者によって同様に使われています。 この言語について詳しくは、[python.org](https://www.python.org) および「[Python for Beginners](https://www.python.org/about/gettingstarted/)」(初心者向けの Python) をご覧ください。

Visual Studio では、Python の開発およびデータ サイエンス ワークロードによる Python 言語の[オープンソース](https://github.com/Microsoft/ptvs) サポート (Visual Studio 2017) および無料の Python Tools for Visual Studio 拡張機能 (Visual Studio 2015 以降) が提供されています。 

[インストール手順](installation.md)の説明に従って Python ワークロードをセットアップした後、以下のリンクを使って Python 関連の機能と Visual Studio 自体の機能について詳しく学習してください。

| 特性 | 説明 | Visual Studio の一般的なドキュメント | 
| --- | --- | --- |
| [Visual Studio のプロジェクト システム](python-projects.md) | Python コードのフォルダー構造を暗黙的に取得し、アプリ コード、テスト コード、Web ページ、JavaScript、ビルド スクリプトなどの識別を明示的に制御できます。 | [Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md) |
| [プロジェクト テンプレート](python-projects.md#project-templates) | コンソール、Web、Azure、データ サイエンス、他の種類のプロジェクト用のプロジェクト構造を短時間で作成します。 | [Visual Studio テンプレート](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| 複数のインタープリターのサポート | さまざまなバージョンの CPython と IronPython をサポートします。 | 適用なし |
| IPython のサポート | インライン プロット、.NET、および Windows Presentation Foundation (WPF) のための REPL での IPython/Jupyter のサポートが含まれます。 | 適用なし |
| [豊富な編集、IntelliSense、コード読解](code-editing.md) | 構文の色分け、すべてのコードとライブラリ間でのオートコンプリート、[コードのフォーマット](code-formatting.md)、シグネチャ ヘルプ、クラス ビュー、定義への移動、すべての参照の検索、コード スニペット、[リファクタリング](code-refactoring.md)、[PyLint](code-pylint.md) などを含みます。 | [コード エディターとテキスト エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md) |
| [対話型ウィンドウ](interactive-repl.md) | コードの一部を簡単に強調表示してそれを対話型ウィンドウに送信する機能を備えた、Python 用のクイック REPL エクスペリエンスを提供します。 | 適用なし |
| [フル機能のデバッグ](debugging.md) | Visual Studio プロジェクトを使っても使わなくてもデバッグを行うことができ、既存の実行可能ファイルに対する機能、[Python/C++ 混合モードのデバッグ](debugging-mixed-mode.md)、Windows/Linux/Mac への[リモート デバッグ](debugging-cross-platform-remote.md)、[Azure へのリモート デバッグ](debugging-azure-remote.md)、および対話型ウィンドウ内でのデバッグを含みます。 | [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md) |
| [包括的なレポートを備えたプロファイリング ツール](profiling.md) | アプリケーション内で時間がどのように費やされているかを調べます。異なるプロファイリング実行の間でパフォーマンスを比較する機能を含みます。 | [プロファイリング ツール](../profiling/profiling-tools.md)(Visual Studio のプロファイリング機能の一部は、Python では使用できません) |
| [単体テスト ツール](unit-testing.md) | Visual Studio テスト エクスプローラーでテストを検出、実行、および管理し、単体テストを簡単にデバッグします。 | [コードの単体テスト](../test/unit-test-your-code.md) |

Python ワークロードに含まれる [Azure SDK for Python](azure-sdk-for-python.md) を使うと Azure サービスを簡単に利用でき、Windows、Mac OS X、Linux のサポートが含まれます。

YouTube で公開されている一連の[概要と詳細に関するビデオ](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)もご覧ください。主な機能の概要がわかります。

[![Python Tools のビデオ](media/video-general.png)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

## <a name="questions-and-answers"></a>質問と回答

**Q.Python で UI を構築するには何を使用できますか?**

A:  この分野の主なツールとして [Qt Project](https://www.qt.io/qt-for-application-development/) があり、[PySide (公式バインディング)](http://wiki.qt.io/PySide) や [PyQt](https://wiki.python.org/moin/PyQt) という Python のバインディングもあります ([PySide のダウンロード ページ](https://download.qt.io/official_releases/pyside/.)も参照してください)。 現在のところ、Visual Studio の Python のサポートには、UI 開発用のツールは含まれていません。

**Q.Python プロジェクトでスタンドアロンの実行可能ファイルを作成できますか?**

A:  一般的に、Python はインタープリター言語であり、Visual Studio や Web サーバーなど、適切な Python 対応環境で、オンデマンドでコードが実行されます。 現在のところ、Python のスタンドアロンの実行可能ファイル (実質的には Python インタープリターが埋め込まれたプログラム) を作成する機能は Visual Studio にありません。 ただし、[StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)で説明されているように、Python コミュニティでは、多様な実行方法が紹介されています。 また、CPython はネイティブ アプリケーション内への埋め込みをサポートしています。詳細については、ブログの投稿「[Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/)」(CPython の埋め込み可能な Zip ファイルの使用方法) を参照してください。

## <a name="features-matrix"></a>機能一覧

[インストール ガイド](installation.md)の説明に従って、以下のエディションの Visual Studio に Python のサポートをインストールできます。

- [Visual Studio 2017 (全エディション)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (全エディション)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- [Visual Studio 2013 Community Edition] (https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx)
- [Visual Studio 2013 Express for Web Update 2 以降](https://www.microsoft.com/en-us/download/details.aspx?id=44912)
- [Visual Studio 2013 Express for Desktop Update 2 以降](https://www.microsoft.com/en-US/download/details.aspx?id=44914)
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
| Web サイトへの Web 配置 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Web ロールへの Web 配置 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| ワーカー ロールへの Web 配置 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
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

6. Windows 8 以降が必要です。 Visual Studio 2013 Express for Web には [プロセスにアタッチ] ダイアログがありませんが、Azure Web サイトのリモート デバッグはサーバー エクスプローラーの [デバッガーのアタッチ] (Python) コマンドを使って可能です。 これには、[Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

7. Windows 8 以降が必要です。 サーバー エクスプローラーの [デバッガーのアタッチ] (Python) コマンドには、[Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

8. Windows 8 以降が必要です。

## <a name="additional-resources"></a>その他の技術情報

- [PyKinect を使った Python での Kinect ゲームの作成](https://github.com/Microsoft/PTVS/wiki/PyKinect) (GitHub wiki)
- [IIS と Python の間の WFastCGI ブリッジ](https://pypi.python.org/pypi/wfastcgi) (python.org)
- - [Microsoft Virtual Academy の無料 Python コース](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)

