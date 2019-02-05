---
title: Windows 上の Visual Studio の Python サポート
titleSuffix: ''
description: Windows 上で最高の Python IDE である Visual Studio の Python 機能 (Python Tools for Visual Studio (PTVS) とも呼ばれます) の概要について説明します
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 699578e564999db55562abaad764cde80fc8b618
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232066"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Windows 上の Visual Studio での Python の使用

Python は、信頼性と柔軟性に優れ、簡単に学ぶことができ、すべてのオペレーティング システムで自由に使える一般的なプログラミング言語であり、強力な開発者コミュニティと多くの無料ライブラリによってサポートされています。 Python は、Web アプリケーション、Web サービス、デスクトップ アプリ、スクリプト、科学技術計算などのすべての開発方法をサポートし、多くの大学、科学者、一般の開発者、プロの開発者によって同様に使われています。 この言語について詳しくは、[python.org](https://www.python.org) および「[Python for Beginners](https://www.python.org/about/gettingstarted/)」(初心者向けの Python) をご覧ください。

Visual Studio は、Windows 上の強力な Python IDE です。 Visual Studio では、**Python の開発**および**データ サイエンス** ワークロードによる Python 言語の[オープンソース](https://github.com/Microsoft/ptvs) サポート (Visual Studio 2017) および無料の Python Tools for Visual Studio 拡張機能 (Visual Studio 2015 以降) が提供されています。

現在、Python は Visual Studio for Mac ではサポートされていませんが、Visual Studio Code によって Mac と Linux でも使うことができます (「[質問と回答](#questions-and-answers)」を参照)。

開始するには:

- [インストール手順](installing-python-support-in-visual-studio.md)に従って、Python ワークロードを設定します。
- この記事の各セクションを読んで、Visual Studio の Python 機能に関する知識を深めてください。 Visual Studio での Python の概要については、[ビデオ シリーズ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) もご覧ください (合計 22 分)。
- 1 つ以上のクイックスタートを使用して、プロジェクトを作成します。 わからない場合は、[Flask を使用して Web アプリを作成する](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)方法から始めます。
- 完全なエンド ツー エンドのエクスペリエンスの場合は、[Visual Studio での Python の使用](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)のチュートリアルに従います。

## <a name="support-for-multiple-interpreters"></a>複数のインタープリターのサポート

Visual Studio の **[Python 環境]** ウィンドウ (以下の図では横幅を広げて表示しています) を使用すると、グローバルな Python 環境、conda 環境、仮想環境をすべて 1 つの場所で管理できます。 Visual Studio では、標準的な場所にある Python のインストールが自動的に検出されます。また、カスタム インストールを構成することができます。 各環境では、簡単にパッケージを管理し、その環境の対話型ウィンドウを開き、環境フォルダーにアクセスできます。

![[Python 環境] ウィンドウを広げた表示](media/environments-expanded-view.png)

**[対話型ウィンドウを開く]** コマンドを使用して、Visual Studio のコンテキスト内で Python を対話的に実行します。 **[PowerShell で開く]** コマンドを使用して、選択した環境のフォルダー内に独立したコマンド ウィンドウを開きます。 そのコマンド ウィンドウから、任意の Python スクリプトを実行できます。

詳細情報

- ビデオ (2 分 35 秒):[Python 環境を管理する](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)
- ドキュメント:[Python 環境を管理する](managing-python-environments-in-visual-studio.md)
- ドキュメント:[Python 環境のリファレンス](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>豊富な編集、IntelliSense、コード読解

Visual Studio には、構文の色分け、すべてのコードとライブラリのオートコンプリート、コードの書式設定、シグネチャ ヘルプ、リファクタリング、lint、型に関するヒントなどを備える最上級の Python エディターが用意されています。 また、Visual Studio には、クラス ビュー、**[定義へ移動]**、**[すべての参照の検索]**、コード スニペットなど、独自の機能もあります。 [対話型ウィンドウ](#interactive-window)と直接統合されているので、既にファイルに保存されている Python コードを簡単に開発することができます。

![Visual Studio での Python コードのオートコンプリート](media/code-editing-completions-simple.png)

詳細情報

- ビデオ (2 分 30 秒):[Python コードの編集](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567)
- ドキュメント:[Python コードの編集](editing-python-code-in-visual-studio.md)
- ドキュメント:[コードの書式設定](formatting-python-code.md)
- ドキュメント:[コードのリファクタリング](refactoring-python-code.md)
- ドキュメント:[リンターの使用](linting-python-code.md)
- 一般的な Visual Studio 機能のドキュメント:[コード エディターの機能](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>対話型ウィンドウ

Visual Studio で認識されるすべての Python 環境で、別のコマンド プロンプトを使用するのではなく、Visual Studio 内で直接、Python インタープリター用の同じ対話型 (REPL) 環境を簡単に開くことができます。 また、環境間を簡単に切り替えることもできます。 (別のコマンド プロンプトを開くには、**[Python 環境]** ウィンドウで目的の環境を選択してから、前述の「[複数のインタープリターのサポート](#support-for-multiple-interpreters)」で説明したように、**[PowerShell で開く]** コマンドを選択します)。

![Visual Studio の Python 対話型ウィンドウ](media/interactive-window.png)

また、Visual Studio では、Python コード エディターと**対話型**ウィンドウ間の緊密な統合も提供されています。 キーボード ショートカットの **Ctrl** + **Enter** キーを使用すると、簡単にエディターの現在のコード行 (またはコード ブロック) を**対話型**ウィンドウに送信し、次の行 (またはブロック) に移動することができます。 **Ctrl** + **Enter** キーを使用すると、デバッガーを実行することなく簡単にコードをステップ実行できます。 また、選択されているコードを同じキー入力で**対話型**ウィンドウに送信し、**対話型**ウィンドウのコードをエディターに簡単に貼り付けることもできます。 これらの機能を組み合わせることで、**対話型**ウィンドウ内のコードのセグメントについて詳しく調べ、エディターで簡単に結果をファイルに保存することができます。

Visual Studio は、インライン プロット、.NET、Windows Presentation Foundation (WPF) など、REPL の IPython/Jupyter もサポートしています。

詳細情報

- ビデオ (2 分 22 秒):[Python Interactive ウィンドウ](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)
- ドキュメント:[対話型ウィンドウ](python-interactive-repl-in-visual-studio.md)
- ドキュメント:[Visual Studio の IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>プロジェクト システム、プロジェクト テンプレート、項目テンプレート

Visual Studio は、時間と共に複雑になるプロジェクトを管理するために役立ちます。 プロジェクトにはフォルダー構造をはるかに超えた機能があり、各ファイルの使用方法や相互の関係などを把握できます。 Visual Studio を使用すると、アプリケーション コード、テスト コード、Web ページ、JavaScript、ビルド スクリプトなどを区別できます。また、ファイルに適した機能が有効になります。 さらに、Visual Studio ソリューションは、Python プロジェクトや C ++ 拡張プロジェクトなどの複数の関連プロジェクトを管理する場合に役立ちます。

![Python プロジェクトと C ++ プロジェクトの両方を含む Visual Studio ソリューション](media/projects-solution-explorer-two-projects.png)

プロジェクト テンプレートと項目テンプレートで、さまざまな種類のプロジェクトやファイルの設定プロセスを自動化すると、貴重な時間を節約し、複雑でエラーが発生しやすい詳細情報の管理作業を軽減できます。 Visual Studio には、Web、Azure、データ サイエンス、コンソールなどの種類のプロジェクト用のテンプレートだけでなく、Python クラス、単体テスト、Azure の Web 構成、HTML、さらには Django アプリなどのファイル用のテンプレートも用意されています。

[![Visual Studio の Python プロジェクト テンプレートと項目テンプレート](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

詳細情報

- ドキュメント:[Python プロジェクトの管理](managing-python-projects-in-visual-studio.md)
- ドキュメント:[項目テンプレートのリファレンス](python-item-templates.md)
- ドキュメント:[Python プロジェクト テンプレート](managing-python-projects-in-visual-studio.md#project-templates)
- ドキュメント:[C++ と Python の使用](working-with-c-cpp-python-in-visual-studio.md)
- 一般的な Visual Studio 機能のドキュメント:[プロジェクト テンプレートと項目テンプレート](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- 一般的な Visual Studio 機能のドキュメント:[Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>フル機能のデバッグ

Visual Studio の長所の 1 つは強力なデバッガーです。 特に Python 用には、Python/C++ 混合モード デバッグ、Linux 上のリモート デバッグ、**対話型**ウィンドウ内のデバッグ、Python の単体テストのデバッグが Visual Studio に含まれています。

![例外をポップアップ表示する Python 用の Visual Studio デバッガー](media/debugging-exception-popup.png)

詳細情報

- ビデオ:[Python のデバッグ (3 分 32 秒)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567)
- ドキュメント:[Python のデバッグ](debugging-python-in-visual-studio.md)
- ドキュメント:[Python と C++ の混合モード デバッグ](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- ドキュメント:[Linux 上のリモート デバッグ](debugging-python-code-on-remote-linux-machines.md)
- 一般的な Visual Studio 機能のドキュメント:[Visual Studio デバッガーの機能ツアー](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>包括的なレポートを備えたプロファイリング ツール

プロファイリングでは、アプリケーション内で時間がどのように使用されているかを調べます。 Visual Studio は、CPython ベースのインタープリターを使用したプロファイリングをサポートし、複数のプロファイリング処理のパフォーマンスを比較する機能を備えています。

[![Visual Studio プロファイラーの Python プロジェクトの結果](media/profiling-results.png)](media/profiling-results.png#lightbox)

詳細情報

- ビデオ:[Python のプロファイリング (3 分 00 秒)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567)
- ドキュメント:[Python のプロファイリング ツール](profiling-python-code-in-visual-studio.md)
- 一般的な Visual Studio 機能のドキュメント:[プロファイリング機能ツアー](../profiling/profiling-feature-tour.md) (Visual Studio のプロファイリング機能の一部は、Python では使用できません)。

## <a name="unit-testing-tools"></a>単体テスト ツール

Visual Studio **テスト エクスプローラー**でテストを検出、実行、および管理し、単体テストを簡単にデバッグします。

![Visual Studio での Python 単体テストのデバッグ](media/unit-test-debugging.png)

詳細情報

- ビデオ:[Python のテスト (2 分 31 秒)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567)
- ドキュメント:[Python 用の単体テスト ツール](unit-testing-python-in-visual-studio.md)
- 一般的な Visual Studio 機能のドキュメント:[コードの単体テスト](../test/unit-test-your-code.md)。

## <a name="azure-sdk-for-python"></a>Azure SDK for Python

Python ワークロードに含まれる Azure SDK for Python を使うと、Windows、Mac OS X、Linux アプリから Azure サービスを簡単に利用できます。

詳細については、[Python 用 Azure SDK](/python/azure/?view=azure-python) に関するページを参照してください。

## <a name="python-training-on-microsoft-virtual-academy"></a>Microsoft Virtual Academy の Python トレーニング

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | <ul><li>[Python によるプログラミングの入門](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Python 初心者:文字列と関数](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Python の基礎:リストとループ](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[よく寄せられる質問](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>質問と回答

**Q.Visual Studio for Mac では Python のサポートを利用できますか?**

A:  まだ実装されていませんが、[開発者コミュニティ](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html)で要望に投票することができます。 [Visual Studio for Mac](/visualstudio/mac/) のドキュメントでは、現在サポートされている開発の種類が示されています。 当面の間、Windows、Mac、Linux での Visual Studio Code は、[利用可能な拡張機能によって Python で問題なく動作します](https://code.visualstudio.com/docs/languages/python)。

**Q.Python で UI を構築するには何を使用できますか?**

A:  この分野の主なツールとして [Qt Project](https://www.qt.io/qt-for-application-development/) があり、[PySide (公式バインディング)](https://wiki.qt.io/PySide) ([PySide のダウンロード ページ](https://download.qt.io/official_releases/pyside/.)もご覧ください) や [PyQt](https://wiki.python.org/moin/PyQt) という Python のバインディングもあります。 現在のところ、Visual Studio の Python のサポートには、UI 開発用のツールは含まれていません。

**Q.Python プロジェクトでスタンドアロンの実行可能ファイルを作成できますか?**

A:  一般的に、Python はインタープリター言語であり、Visual Studio や Web サーバーなど、適切な Python 対応環境で、オンデマンドでコードが実行されます。 現在のところ、Python のスタンドアロンの実行可能ファイル (実質的には Python インタープリターが埋め込まれたプログラム) を作成する機能は Visual Studio にありません。 ただし、[StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)で説明されているように、Python コミュニティでは、実行可能ファイルを作成するさまざまな方法が提供されています。 また、CPython はネイティブ アプリケーション内への埋め込みをサポートしています。詳細については、ブログの投稿「[Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/)」(CPython の埋め込み可能な Zip ファイルの使用方法) をご覧ください。

## <a name="features-matrix"></a>機能一覧

[インストール ガイド](installing-python-support-in-visual-studio.md)の説明に従って、以下のエディションの Visual Studio に Python の機能をインストールできます。

- [Visual Studio 2017 (全エディション)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2015 (全エディション)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express for Web Update 2 以降
- Visual Studio 2013 Express for Desktop Update 2 以降
- Visual Studio 2013 (Pro エディション以上)
- Visual Studio 2012 (Pro エディション以上)
- Visual Studio 2010 SP1 (Pro エディション以上、.NET 4.5 が必要)

Visual Studio 2015 およびそれ以前のバージョンは、[visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/) で入手できます。

> [!Important]
> 機能が完全にサポートおよび保守されるのは、Visual Studio の最新バージョンのみです。 古いバージョンでも機能を使うことはできますが、積極的には保守されません。

|          Python のサポート          |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   複数のインタープリターの管理   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| 一般的なインタープリターの自動検出 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     カスタム インタープリターの追加      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       仮想環境       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip/簡易インストール         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|         プロジェクト システム         |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| 既存のコードから新しいプロジェクトを作成 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         すべてのファイルを表示         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         ソース管理         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Git 統合         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>


|           編集            |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     構文の強調表示      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        オートコンプリート         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        シグネチャ ヘルプ        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          クイック ヒント          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  オブジェクト ブラウザー/クラス ビュー   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        [ナビゲーション バー]        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       定義へ移動       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         移動          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     [すべての参照の検索]      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       自動インデント       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       コードのフォーマット        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      リファクタリング - 名前の変更       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  リファクタリング - メソッドの抽出   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| リファクタリング - インポートの追加と削除 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|     対話型ウィンドウ     |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     対話型ウィンドウ     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| インライン グラフを含む IPython | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|               デスクトップ               |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     コンソール/Windows アプリケーション     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (XAML デザイナーを含む) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows フォーム       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|         Web         |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Django Web プロジェクト  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Bottle Web プロジェクト  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask Web プロジェクト  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| 汎用 Web プロジェクト | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|         Azure          |   2017   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Web サイトへの配置   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Web ロールへの配置   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| worker ロールへの配置  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Azure エミュレーターでの実行  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    リモート デバッグ    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| サーバー エクスプローラーのアタッチ | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>


|           Django テンプレート           |   2017   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              デバッグ               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            オートコンプリート             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| CSS と JavaScript のオートコンプリート | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>


|                  デバッグ                  |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  デバッグ                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         プロジェクトを使わないデバッグ         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        デバッグ - 編集へのアタッチ        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            混合モードのデバッグ             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| リモート デバッグ (Windows、Mac OS X、Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          対話型ウィンドウのデバッグ           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>


| プロファイル |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| プロファイル | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>


|     テスト      |   2017   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| テスト エクスプローラー | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   テストの実行    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  テストのデバッグ   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Visual Studio 2012 の Git サポートは、[Visual Studio ギャラリー](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)で入手できる Visual Studio Tools for Git 拡張機能で利用可能です。

1. Azure Web サイトに配置するには、[Azure SDK for .NET 2.1 - Visual Studio 2010 SP1](https://go.microsoft.com/fwlink/?LinkId=313855) が必要です。 以降のバージョンは Visual Studio 2010 をサポートしません。

1. Azure Web ロールおよびワーカー ロールのサポートには、[Azure SDK for .NET 2.3 - VS 2012](https://go.microsoft.com/fwlink/?LinkId=323511) 以降が必要です。

1. Azure Web ロールおよびワーカー ロールのサポートには、[Azure SDK for .NET 2.3 - VS 2013](https://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

1. Visual Studio 2013 の Django テンプレート エディターには、Update 2 をインストールすることで解決される既知の問題がいくつかあります。

1. Windows 8 以降が必要です。 Visual Studio 2013 Express for Web には **[プロセスにアタッチ]** ダイアログがありませんが、Azure Web サイトのリモート デバッグは、**サーバー エクスプローラー**の **[デバッガーのアタッチ(Python)]** コマンドを使って実行可能です。 リモート デバッグには、[Azure SDK for .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

1. Windows 8 以降が必要です。 **サーバー エクスプローラー**の **[デバッガーのアタッチ(Python)]** コマンドには、[Azure SDK for .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) 以降が必要です。

1. Windows 8 以降が必要です。

## <a name="additional-resources"></a>その他の技術情報

- [IIS と Python の間の WFastCGI ブリッジ](https://pypi.org/p/wfastcgi) (pypi.org)
- [Microsoft Virtual Academy の無料 Python コース](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Python に関して寄せられることの多い質問 (Microsoft Virtual Academy)](https://aka.ms/mva-top-python-questions)
