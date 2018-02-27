---
title: "Visual Studio での Python 環境の管理 | Microsoft Docs"
description: "Visual Studio の [Python 環境] ウィンドウを使って、グローバル環境と仮想環境を管理する方法や、カスタム環境の設定方法、Python インタープリターのインストール、パッケージのインストール、検索パスの設定、Visual Studio プロジェクトの環境の管理について説明します。"
ms.custom: 
ms.date: 02/13/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6abf950f7af86bf65b14752bd1cd9df4a6e292e5
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="python-environments"></a>Python 環境

Python *環境*は、Python コードを実行するコンテキストです。 1 つの環境は、インタープリター、ライブラリ (通常は Python 標準ライブラリ)、およびインストールされているパッケージのセットで構成されます。 これらのコンポーネントがすべて合わさって、有効な言語の構造と構文、アクセスできるオペレーティング システム機能、使用できるパッケージが決まります。

この記事で説明するように、Visual Studio では、[[Python 環境] ウィンドウ](#managing-python-environments-in-visual-studio)を使って環境をすべて管理できます。 特定のプロジェクトに対して、使用する環境を選択できます。その環境では、コードの実行、デバッグ、構文のチェック、インポートやメンバーの入力候補の表示を行うほか、インタープリターやインストールされているライブラリに固有のその他のタスクを行います。 また、Visual Studio では、コード入力時のオートコンプリートを提供する環境ごとに IntelliSense データベースが保持されます。

さらに Visual Studio では、仮想環境、`requirements.txt` ファイル、および検索パスもサポートされます。

**注**: Visual Studio で Python を初めて使用される場合は、次の記事で必要な予備知識についてご確認ください。

- [Visual Studio での Python の使用](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio での Python サポートのインストール](installing-python-support-in-visual-studio.md)

## <a name="global-and-virtual-environments"></a>グローバル環境と仮想環境

Python 環境には、グローバル環境と仮想環境の 2 種類があります。

**グローバル環境**: 各 Python インストールで (Python 2.7、Python 3.6、Anaconda 4.4.0 など。「[Python インタープリターの選択とインストール](#selecting-and-installing-python-interpreters)」を参照) 独自の環境が保持されます。 各環境は、特定の Python インタープリター、その標準ライブラリ、および事前インストールされたパッケージのセットで構成されます。 グローバル環境にパッケージをインストールすると、グローバル環境を使用するすべてのプロジェクトでパッケージが使用できるようになります。 グローバル環境がファイル システムの保護領域にある場合 (`c:\program files` など)、パッケージをインストールするには管理者特権が必要です。

グローバル環境は、コンピューター上のすべてのプロジェクトで使用できます。 Visual Studio では、1 つのグローバル環境を既定の環境として選択します。プロジェクトに対して別の環境を特に選ばない限り、すべてのプロジェクトでこれが使用されます。 詳細については、「[プロジェクト用の環境の選択](#selecting-an-environment-for-a-project)」をご覧ください。

**仮想環境**: グローバル環境にインストールされたパッケージは、グローバル環境を使うすべてのプロジェクトで使用できるため、2 つのプロジェクトで、互換性のないパッケージや同じパッケージの異なるバージョンが必要な場合、競合が発生する可能性があります。 仮想環境では、このような競合を避けるために、グローバル環境のインタープリターと標準ライブラリを使用しながら、分離フォルダーで独自のパッケージ ストアを保持します。

Visual Studio では、特定のプロジェクト用の仮想環境を作成可能で、これはプロジェクトのサブフォルダーに格納されます (「[仮想環境の作成](#creating-virtual-environments)」を参照)。 プロジェクト ファイルもこの仮想環境を識別します。 また、Visual Studio では、その仮想環境にインストールしたすべてのパッケージがプロジェクトの `requirements.txt` ファイルに記録されます。 プロジェクトを共有していて、他の開発者が各自のコンピューターでプロジェクトを開く場合、Visual Studio では、仮想環境を再作成するためのオプションを使用できます。

### <a name="selecting-and-installing-python-interpreters"></a>Python インタープリターの選択とインストール

既定では、Visual Studio 2017 に Python 開発ワークロードをインストールすると、Python 3 (64 ビット) もインストールされます。 [インストール](installing-python-support-in-visual-studio.md)に関する記事で説明されているように、必要に応じて、32 ビットおよび 64 ビット バージョンの Python 2、Python 3、Anaconda 2、および Anaconda 3 のインストールも選択できます。 次の表に示すインタープリターはいずれも手動でインストールすることもできます。インストールされたものは Visual Studio によって検出されます。 (たとえば、Visual Studio をインストールする前に Anaconda 3 がインストールされている場合、Visual Studio インストーラーでそれを再度インストールする必要はありません)

Visual Studio 2015 以前では、いずれかのインタープリターを手動でインストールする必要があります。

Visual Studio (すべてのバージョン) では、(「[PEP 514 - Python registration in the Windows registry (PEP 514 - Windows レジストリでの Python の登録)](https://www.python.org/dev/peps/pep-0514/)」に従って) レジストリをチェックし、インストール済みの各 Python インタープリターの環境が自動的に作成されます。 Visual Studio でインストール済みの環境が検出されない場合は、「[既存インタープリター用の環境の作成](#creating-an-environment-for-an-existing-interpreter)」をご覧ください。

| インタープリター | 説明 |
| --- | --- |
| [CPython](https://www.python.org/) | "ネイティブ" で最もよく使われるインタープリターであり、32 ビット バージョンと 64 ビット バージョンがあります (32 ビットを推奨)。 最新の言語機能、Python パッケージの最大限の互換性、完全なデバッグ サポート、および [IPython](http://ipython.org/) との相互運用性が含まれています。 「[Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3)」(Python 2 と Python 3 のどちらを使うか) もご覧ください。 Visual Studio 2015 以前では、Python 3.6 をサポートしていないため、"Python バージョン 3.6 はサポートされていません" エラーが発生する場合があることに注意してください。 代わりに 3.5 以前の Python を使用します。 |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python の .NET の実装であり (32 ビット バージョンと 64 ビット バージョン)、C#/F#/Visual Basic の相互運用機能、.NET API へのアクセス、標準 Python デバッグ (ただし、C++ 混合モードのデバッグはありません)、IronPython/C# の混合デバッグが提供されます。 ただし、IronPython は仮想環境をサポートしていません。 |
| [Anaconda](https://www.continuum.io) | Python を利用するオープン データ サイエンス プラットフォームであり、最新バージョンの CPython と、インストールが困難なパッケージのほとんどを含みます。 他のインタープリターに決定できない場合にお勧めします。 |
| [PyPy](http://www.pypy.org/) | Python の高パフォーマンスなトレースの JIT 実装であり、実行時間の長いプログラム、およびパフォーマンスに問題があるが他の解決策が見つからない場合に、適しています。 Visual Studio で動作しますが、高度なデバッグ機能のサポートには制限があります。 |
| [Jython](http://www.jython.org/) | Java 仮想マシン (JVM) での Python の実装です。 IronPython に似ており、Jython で実行されるコードは Java のクラスおよびライブラリとやり取りできますが、CPython 用の多くのライブラリは使用できない場合があります。 Visual Studio で動作しますが、高度なデバッグ機能のサポートには制限があります。 |

Python 環境用に新しい検出形式を提供したい開発者は、「[PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments)」(PTVS 環境の検出) (github.com) をご覧ください。

## <a name="managing-python-environments-in-visual-studio"></a>Visual Studio での Python 環境の管理

[Python 環境] ウィンドウを開くには、**[表示] > [その他のウィンドウ] > [Python 環境]** の順にメニュー コマンドを選択するか、ソリューション エクスプローラーでプロジェクトの **[Python 環境]** ノードを右クリックして **[すべての Python 環境を表示]** を選択します。

    ![View All Environments command in Solution Explorer](media/environments-view-all.png)

いずれの場合も、[Python Environments (Python 環境)] ウィンドウはソリューション エクスプローラーの兄弟タブとして表示されます。

![[Python Environments (Python 環境)] ウィンドウ](media/environments-default-view.png)

上の例は、Python 3.4 (32 ビット CPython) と共に IronPython 2.7 の 32 ビットおよび 64 ビット バージョンがインストールされることを示しています。 太字で表示される既定の環境は Python 3.4 で、これはすべての新しいプロジェクトで使われます。 環境が何も表示されない場合は、Visual Studio 2015 以降に Python Tools for Visual Studio はインストールされていますが、Python インタープリターはインストールされていないことを意味します (前の「[Python インタープリターの選択とインストール](#selecting-and-installing-python-interpreters)」を参照)。 **[+ カスタム...]** コマンドを使用して、[既存インタープリターの環境を作成](#create-an-environment-for-an-existing-interpreter)できます。

> [!Tip]
> python.org からのインストーラーを使用することによる Python 2.7.11 から Python 2.7.14 へのアップグレードなど、既存のインタープリターに対する更新プログラムを検出します。インストール プロセス中には、古くなった環境が **Python 環境**のリストから消え、その場所に更新プログラムが表示されます。

表示されている各環境の右側に、その環境の対話型のウィンドウを開くコントロールがあります。 環境の IntelliSense データベースを更新する別のコントロールが表示されることもあります。

環境の一覧の下のドロップダウン セレクターには、**[概要]**、**[パッケージ]**、および **[IntelliSense]** の各オプションが表示されます。これらのオプションについては、このセクションで後述します。 **[Python 環境]** ウィンドウを大きく広げると、これらのオプションがタブとして表示され、より操作しやすくなります。

![[Python Environments (Python 環境)] ウィンドウを広げた表示](media/environments-expanded-view.png)

> [!Note]
> Visual Studio はシステム サイト パッケージのオプションを尊重しますが、Visual Studio 内からそれを変更する方法は用意されていません。

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | Visual Studio での Python 環境については、[こちらのビデオ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) をご覧ください (2 分 35 秒)。|

### <a name="creating-an-environment-for-an-existing-interpreter"></a>既存インタープリター用の環境の作成

Visual Studio でインタープリターが検出されない場合は (標準以外の場所にインストールされている場合など)、以下の手順で環境を作成できます。

1. [[Python Environments]\(Python 環境\) ウィンドウ](#managing-python-environments-in-visual-studio)で **[+ Custom...]\(+ カスタム...\)** を選択します。これで、新しい環境が作成されて、[**[Configure]\(構成\)** タブ](#configure-tab)が開きます (後で説明します)。

    ![新しいカスタム環境の既定のビュー](media/environments-custom-1.png)

1. **[Description (説明)]** フィールドに環境の名前を入力します。
1. **[Prefix path (プレフィックスのパス)]** フィールドでは、インタープリターのパスを入力するか参照します。
1. **[Auto Detect (自動検出)]** を選んで Visual Studio に残りのフィールドを設定させるか、または手動で設定します。
1. **[Apply (適用)]** を選んで環境を保存します。
1. 環境を削除する場合は、**[Configure (構成)]** タブの **[Remove (削除)]** コマンドを選びます。自動検出された環境ではこのオプションは提供されません。 詳細については、次のセクションを参照してください。

### <a name="moving-an-existing-interpreter"></a>既存のインタープリターの移動

既存のインタープリターをファイル システム上の新しい場所に移動すると、Visual Studio はこの変更を自動的に検出しません。手動で環境を更新する必要があります。

- そのインタープリターの環境を最初に作成した場合は、新しい場所を指すようにその環境を編集します。

- 環境が最初に自動検出された場合、Visual Studio で調べるレジストリ エントリを作成した別のインストーラー プログラムでコンピューターにインストールされています。 この場合は、まず、Python インタープリターを元の場所に復元します。 次に、インストーラーを使用してアンインストールします。これで、レジストリ エントリがクリアされます。 次に、目的の場所にインタープリターを再インストールします。 Visual Studio を再起動すると、新しい場所が自動検出されます。 このプロセスによって、確実にインストーラーの他の副作用が正しく適用されます。

### <a name="overview-tab"></a>[Overview (概要)] タブ

環境の基本的な情報とコマンドを提供します。

![[Python Environments (Python 環境)] の [Overview (概要)] タブ](media/environments-overview-tab.png)

| コマンド | 説明 |
| --- | --- |
| Make this environment the default for new projects (この環境を新しいプロジェクトの既定にする) | アクティブな環境を設定します。これにより、IntelliSense データベースが読み込まれる間、Visual Studio がしばらく応答しなくなる場合があります。 多くのパッケージがある環境では、長時間応答しなくなる可能性があります。 |
| ディストリビューターの Web サイトに移動する | Python のディストリビューションで提供された URL をブラウザーで開きます。 たとえば、Python 3.x では python.org に移動します。 |
| 対話型ウィンドウを開く | この環境用の[対話型 (REPL) ウィンドウ](python-interactive-repl-in-visual-studio.md)を Visual Studio 内で開き、すべての[スタートアップ スクリプト (後述)](#startup-scripts) を適用します。 |
| 対話型のスクリプトを確認する | 「[スタートアップ スクリプト](#startup-scripts)」をご覧ください。 |
| IPython 対話モードを使用する | 設定すると、IPython では対話型ウィンドウが既定で開きます。 インライン プロットおよびヘルプを表示する `name?` やシェル コマンド用の `!command` などの拡張 IPython 構文が有効になります。 Anaconda ディストリビューションを使うときは、追加パッケージが必要なので、このオプションを使うことをお勧めします。 詳しくは、「[対話型ウィンドウでの IPython の使用](interactive-repl-ipython.md)」をご覧ください。 |
| PowerShell で開く | PowerShell コマンド ウィンドウでインタープリターを開始します。 |
| (フォルダー リンク) | 環境のインストール フォルダー、python.exe インタープリター、pythonw.exe インタープリターに簡単にアクセスできます。 インストール フォルダーはエクスプローラーで開き、2 つのインタープリターはコンソール ウィンドウが開きます。 |

#### <a name="startup-scripts"></a>スタートアップ スクリプト

日常のワークフローで対話型ウィンドウを使っていると、ヘルパー関数を作成して繰り返し使うことがあります。 たとえば、Excel でデータ フレームを開く関数を作成し、そのコードをスタートアップ スクリプトとして保存して、対話型ウィンドウでいつでも使えるようにするといった場合です。

スタートアップ スクリプトにはインポート、関数定義、その他文字どおりどのようなコードでも含めることができ、対話型ウィンドウは自動的にそれを読み込んで実行します。 このようなスクリプトは、2 つの方法で参照されます。

1. 環境をインストールすると、Visual Studio は `Documents\Visual Studio 2017\Python Scripts\<environment>` フォルダーを作成します。&lt;environment&gt; は、環境の名前と同じです。 **[対話型のスクリプトを確認する]** コマンドを使って、環境固有のフォルダーに簡単に移動できます。 その環境の対話型ウィンドウを開始すると、このフォルダーで見つかったすべての `.py` ファイルがアルファベット順に読み込まれて実行されます。

1. **[ツール] > [オプション] > [Python ツール] > [対話型ウィンドウ]** タブ (「[対話型ウィンドウ オプション](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)」を参照) の**[スクリプト]** コントロールでは、すべての環境で読み込まれて実行されるスタートアップ スクリプトの追加フォルダーを指定します。 ただし、この機能は現時点では機能しません。

### <a name="configure-tab"></a>[Configure (構成)] タブ

次の表で説明するような詳細が表示されます。 このタブが存在しない場合は、Visual Studio がすべての詳細情報を自動的に管理していることを意味します。

![[Python Environments (Python 環境)] の [Configure (構成)] タブ](media/environments-configure-tab.png)

| フィールド | 説明 |
| --- | --- |
| **説明** | 環境の名前です。 |
| **Prefix path (プレフィックスのパス)** | インタープリターの基本フォルダーの場所です。 この値を入力して **[自動検出]** をクリックすると、Visual Studio が他のフィールドを設定します。 |
| **Interpreter Path (インタープリターのパス)** | インタープリターの実行可能ファイルへのパスです。通常は、プレフィックスのパスの後に `python.exe` を付けたものです。 |
| **Windowed interpreter (ウィンドウ形式のインタープリター)** | コンソールではない実行可能ファイルへのパスです。多くの場合、プレフィックスのパスの後に `pythonw.exe` を付けたものです。 |
| **Library path (ライブラリのパス)** | 標準ライブラリのルートを指定します。ただし、Visual Studio がさらに正確なパスをインタープリターに要求できる場合、この値は無視される可能性があります。 |
| **Language version (言語バージョン)** | ドロップダウン メニューから選びます。 |
| **アーキテクチャ** | 通常は自動的に検出されて設定されます。されない場合は 32 ビットまたは 64 ビットを指定します。 |
| **Path environment variable (パス環境変数)** | 検索パスを探すためにインタープリターが使う環境変数です。 Visual Studio は、Python を開始するとき、プロジェクトの検索パスが含まれるように変数の値を変更します。 通常、このプロパティは `PYTHONPATH` に設定する必要がありますが、一部のインタープリターでは別の値が使われます。 |

### <a name="pip-tab"></a>[pip] タブ

環境にインストールされているパッケージを管理します。それにより、ユーザーは新しいパッケージ (すべての依存関係を含む) の検索とインストールもできるようになります。 検索機能は、現在インストールされているパッケージと [PyPI](https://pypi.python.org) をフィルター処理します。 検索ボックスに、`pip install` コマンドと `--user` や `--no-deps` などのフラグを直接入力することもできます。

![[Python Environments (Python 環境)] の [pip] タブ](media/environments-pip-tab.png)

パッケージをインストールすると、ファイル システム上の環境の `Lib` フォルダー内にサブフォルダーが作成されます。 たとえば、Python 3.6 を `c:\Python36` にインストールすると、パッケージは `c:\Python36\Lib` にインストールされます。Anaconda3 を `c:\Program Files\Anaconda3` にインストールすると、パッケージは `c:\Program Files\Anaconda3\Lib` にインストールされます。

後者の場合、ファイル システムの保護された領域 `c:\Program Files` に環境があるため、Visual Studio は、パッケージ サブフォルダーを作成できるように、管理者特権で `pip install` を実行する必要があります。 管理者特権への昇格が必要な場合、Visual Studio により "この環境でパッケージのインストール、更新、削除を行うには、管理者特権が必要な場合があります" というプロンプトが表示されます。

![パッケージ インストールのための昇格時のプロンプト](media/environments-pip-elevate.png)

**[今すぐ昇格]** を選ぶと、1 回の操作について pip に管理者特権が付与され、アクセス許可を求めるオペレーティング システムのプロンプトも対象になります。 **[管理者特権なしで続行]** を選ぶと、パッケージのインストールは試みられますが、pip がフォルダーを作成しようとすると、"エラー: 'C:\Program Files\Anaconda3\Lib\site-packages\png.py' を作成できませんでした: アクセス許可が拒否されました" のような出力で失敗します。

**[パッケージのインストール時か削除時に必ず昇格]** を選ぶと、対象の環境ではダイアログが表示されなくなります。 再びダイアログが表示されるようにするには、**[ツール] > [オプション] > [Python ツール] > [全般]** に移動し、**[永続的に表示されないすべてのダイアログをリセットする]** ボタンを選びます。

同じオプション タブでは、**[常に管理者として pip を実行する]** を選んで、すべての環境でダイアログを非表示にすることもできます。 「[Options - General tab](python-support-options-and-settings-in-visual-studio.md#general-options)」([全般] タブのオプション) をご覧ください。

### <a name="intellisense-tab"></a>[IntelliSense] タブ

IntelliSense 入力候補データベースの現在の状態を示します。

![[Python Environments (Python 環境)] の [IntelliSense] タブ](media/environments-intellisense-tab.png)

データベースには環境内のすべてのライブラリのメタデータが含まれ、IntelliSense の速度が向上しメモリ使用量が減ります。 Visual Studio は新しい環境を検出すると (またはユーザーが追加すると)、ライブラリのソース ファイルを分析することで、データベースのコンパイルを自動的に開始します。 インストールされている内容により、この処理には 1 分から 1 時間以上かかることがあります (たとえば、Anaconda には多くのライブラリが付属しており、データベースのコンパイルに少し時間がかかります)。完了すると、詳細な IntelliSense が提供され、新しいライブラリをインストールするまでデータベースを再度更新する (**[Refresh DB]\(DB の更新\)** ボタンで) 必要はありません。

データがコンパイルされていないライブラリには、**!** が表示されます。環境のデータベースが完成していない場合は、**!** も メイン環境リストのライブラリの横に表示されます。

## <a name="selecting-an-environment-for-a-project"></a>プロジェクト用の環境の選択

プロジェクト固有環境を指定すると、プロジェクトは常にその特定の環境で実行され、既定のグローバル環境は無視されます。 たとえば、グローバル既定環境が CPython である場合に、IronPython と、グローバル環境にインストールされていない特定のライブラリがプロジェクトで必要なときは、プロジェクト固有環境が必要になります。

プロジェクト環境は、ソリューション エクスプローラーの [Python Environments (Python 環境)] ノードに一覧表示されます。 太字のエントリは現在アクティブであり、デバッグ、インポートとメンバー入力候補、構文チェック、および環境を必要とするその他のタスクに使われます。

![ソリューション エクスプローラーに表示されたプロジェクト環境](media/environments-project.png)

プロジェクトに対して別の環境をアクティブ化するには、その環境を右クリックして、**[Activate Environment (環境のアクティブ化)]** を選びます。

**[Python Environments (Python 環境)]** を右クリックして **[Add/Remove Python Environments... (Python 環境の追加/削除...)]** を選ぶことで、任意のグローバル環境をプロジェクト環境として追加できます。表示される一覧で、プロジェクトで使用可能な環境を選択または選択解除できます。

![[Add/Remove Python Environments (Python 環境の追加/削除)] ダイアログ](media/environments-add-remove.png)

ソリューション エクスプローラーでは、環境を展開して、インストールされているパッケージ (環境をアクティブにすると、コードでインポートして使用できるもの) を表示することもできます。

![ソリューション エクスプローラーでの環境の Python パッケージ](media/environments-installed-packages.png)

新しいパッケージをインストールするには、環境を右クリックし、**[Install Python Package... (Python パッケージのインストール...)]** を選んで、目的のパッケージの名前を入力します。 パッケージ (および依存関係) は [Python Package Index (PyPI)](https://pypi.python.org/pypi) からダウンロードされます。ここでパッケージを検索することもできます。 Visual Studio のステータス バーと出力ウィンドウには、インストールに関する情報が表示されます。 パッケージをアンインストールするには、パッケージを右クリックして **[Remove (削除)]** を選びます。

> [!Note]
> Python のパッケージ管理サポートは、現在、Python のコア開発チームによって開発中です。 表示されるエントリは常に正確であるとは限らず、インストールとアンインストールが信頼できない場合、または使用できない場合があります。 Visual Studio は、使用可能な場合は pip パッケージ マネージャーを使い、必要な場合はダウンロードしてインストールします。 Visual Studio は、easy_install パッケージ マネージャーを使うこともできます。 コマンド ラインから pip または easy_install を使ってインストールされたパッケージも表示されます。

> [!Tip]
> pip がパッケージのインストールに失敗する一般的な状況は、パッケージの `*.pyd` ファイルにネイティブ コンポーネントのソース コードが含まれる場合です。 必要なバージョンの Visual Studio がインストールされていない場合、pip はこれらのコンポーネントをコンパイルできません。 このような状況では、"`error: Unable to find vcvarsall.bat`" というエラー メッセージが表示されます。 多くの場合、`easy_install` ではコンパイル済みのバイナリをダウンロードでき、Python の古いバージョンに適したコンパイラは [http://aka.ms/VCPython27](http://aka.ms/VCPython27) からダウンロードできます。 詳しくは、Python Tools チーム ブログの「[How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/)」("vcvarsallbat が見つからない" という問題への対処方法) をご覧ください。

## <a name="creating-virtual-environments"></a>仮想環境の作成

1. ソリューション エクスプローラーで **[Python Environments (Python 環境)]** を右クリックし、**[Add Virtual Environment... (仮想環境の追加...)]** を選びます。次のダイアログが表示されます。

    ![仮想環境の作成](media/environments-add-virtual-1.png)

1. 名前を指定してプロジェクトのパスに仮想環境を作成するか、または完全なパスを指定して他の場所に作成します  (他のツールとの最大限の互換性を確保するには、名前ではアルファベットと数字のみを使います)。

1. 基本インタープリターとしてグローバル環境を選び、**[Create (作成)]** をクリックします。 `pip` と `virtualenv` または `venv` パッケージが使用できない場合は、ダウンロードされてインストールされます。

    指定したパスが既存の仮想環境の場合は、基本インタープリターが検出されて、[作成] ボタンは **[追加]** に変わります。

    ![既存の仮想環境の追加](media/environments-add-virtual-2.png)

ソリューション エクスプローラーで **[Python Environments (Python 環境)]** を右クリックし、**[Add Existing Virtual Environment... (既存の仮想環境の追加...)]** を選ぶことで、既存の仮想環境を追加することもできます。Visual Studio は、環境の `lib` ディレクトリにある `orig-prefix.txt` ファイルを使って、基本インタープリターを自動的に検出します。

プロジェクトに追加された仮想環境は **[Python Environments (Python 環境)]** ウィンドウに表示され、他の環境と同じように、アクティブ化してパッケージを管理できます。 仮想環境を右クリックして **[削除]** を選ぶと、環境への参照が削除されるか、または環境とディスク上のすべてのファイルが削除されます (ただし、基本インタープリターは削除されません)。

仮想環境の欠点として、ハード コーディングされたファイル パスを含むため、他の開発用コンピューターとの間で簡単に共有や転送ができないことに注意してください。 ただし、次のセクションで説明するように、`requirements.txt` ファイルを使うと、プロジェクトの受信者は簡単に環境を復元できます。

## <a name="managing-required-packages-requirementstxt"></a>必要なパッケージの管理 (requirements.txt)

ビルド システムを使用してプロジェクトを他のユーザーと共有する場合、または [Microsoft Azure でのプロジェクトの公開](python-azure-cloud-service-project-template.md)を予定している場合は、プロジェクトで必要な外部パッケージを指定する必要があります。 推奨されるアプローチとしては、依存パッケージの必要なバージョンをインストールする pip のためのコマンド リストを含む [requirements.txt ファイル](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) を使います。

技術的には、任意のファイル名を使って要件を追跡できますが (パッケージをインストールするときに `-r <full path to file>` を使って)、Visual Studio では `requirements.txt` に固有のサポートが用意されています。

- `requirements.txt` を含むプロジェクトを読み込み、そのファイルにリストされているすべてのパッケージをインストールする場合は、**ソリューション エクスプローラー**で **[Python 環境]** ノードを展開し、環境ノードを右クリックして **[requirements.txt からインストール]** を選択します。

    ![requirements.txt からインストールする](media/environments-requirements-txt-install.png)

- 既に必要なすべてのパッケージをプロジェクトにインストールしている場合は、ソリューション エクスプローラーで環境を右クリックして、**[requirements.txt を生成]** を選択することで、必要なファイルを作成できます。 ファイルが既に存在する場合、更新方法の指定を求められます。

    ![requirements.txt の更新オプション](media/environments-requirements-txt-replace.png)

  - **[Replace entire file (ファイル全体を置き換える)]** は、存在するすべてのアイテム、コメント、オプションを削除します。
  - **[既存のエントリを更新]** は、パッケージの要件を検出し、現在インストールされているバージョンと一致するようにバージョン指定子を更新します。
  - **[Update and add entries (エントリを更新および追加する)]** は、検出されたすべての要件を更新し、他のすべてのパッケージをファイルの末尾に追加します。

`requirements.txt` ファイルはプロジェクトの要件を固定するためのものなので、インストールされるすべてのパッケージが正確なバージョンと共に記述されています。 正確なバージョンを使うと、別のコンピューターに環境を簡単に再現できます。 バージョンの範囲、別のパッケージの依存関係、または pip 以外のインストーラーでインストールされたパッケージであってもも、含まれています。

新しい仮想環境を追加する場合に `requirements.txt` ファイルが存在していると、**[仮想環境の追加]** ダイアログにパッケージを自動的にインストールするオプションが表示されるため、別のコンピューターに簡単に環境を再作成できます。

![requirements.txt で仮想環境を作成する](media/environments-requirements-txt.png)

pip でインストールできないパッケージが `requirements.txt` ファイルに出現する場合は、インストール全体が失敗します。 その場合は、ファイルを手動で編集してこのパッケージを除外するか、[pip のオプション](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)を使ってパッケージのインストール可能なバージョンを参照するようにします。 たとえば、[`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) を使って依存関係をコンパイルし、`--find-links <path>` オプションを `requirements.txt` に追加することができます。

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>検索パス

通常の Python の使用方法では、`PYTHONPATH` 環境変数 (または `IRONPYTHONPATH` など) がモジュール ファイルの既定の検索パスを提供します。 つまり、`from <name> import...` または `import <name>` ステートメントを使うと、Python は次の場所を順に検索して、一致する名前を探します。

1. Python の組み込みモジュール
1. 実行している Python コードが含まれるフォルダー
1. 該当する環境変数によって定義された "モジュール検索パス" (Python のコア ドキュメントの「[The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)」(モジュール検索パス) および「[Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH)」(環境変数) をご覧ください)。

ただし、検索パス環境変数がシステム全体に対して設定されている場合でも、Visual Studio はこの変数を無視します。 実際はまさにシステム全体が設定されている "*ために*" 無視されるので、自動的には答えられないようなある種の疑問が発生します。参照されているモジュールは Python 2.7 または Python 3.3 のどちらか。 標準ライブラリ モジュールをオーバーライドするのか。 開発者はこの動作を認識しているのか、それとも悪意のあるハイジャックの試みか。

そのため Visual Studio では、環境とプロジェクトの両方で検索パスを直接指定するための手段が用意されています。 Visual Studio で実行またはデバッグするコードは、検索パスを `PYTHONPATH` (およびその他の同等の変数) の値で受け取ります。 検索パスを追加すると、Visual Studio はそれらの場所でライブラリを検査し、IntelliSense データベースを構築します (ライブラリの数によっては時間がかかります)。

検索パスを追加するには、ソリューション エクスプローラーで **[Search Paths (検索パス)]** 項目を右クリックし、**[Add Folder to Search Path... (検索パスへのフォルダーの追加...)]** を選んで、含めるフォルダーを選びます。 このパスは、プロジェクトに関連付けられているすべての環境に使われます。 (環境が Python 3 ベースの場合に、検索パスを Python 2.7 モジュールに追加しようとすると、エラーが発生することがあります。)

**[Add Zip Archive to Search Path... (検索パスへの Zip アーカイブの追加...)]** を選ぶことで、拡張子が `.zip` または `.egg` のファイルを検索パスとして追加することもできます。フォルダーと同様に、これらのファイルの内容もスキャンされて、IntelliSense に利用されます。

常に同じ検索パスを使い、内容があまり変化しない場合は、サイトパッケージ フォルダーにインストールする方が効率的な場合があります。 検索パスは分析されて IntelliSense データベースに格納され、常に適切な環境に関連付けられるため、各プロジェクトに検索パスを追加する必要はありません。
