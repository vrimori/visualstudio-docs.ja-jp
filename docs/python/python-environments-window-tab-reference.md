---
title: '[Python 環境] ウィンドウのリファレンス | Microsoft Docs'
description: Visual Studio の [Python 環境] ウィンドウに表示される各タブの詳細について説明します。
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f323bfbe65a5e25935673674e604425bc33185c
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="python-environments-window-tabs-reference"></a>[Python 環境] ウィンドウ タブ リファレンス

**[Python 環境]** ウィンドウを開くには:

- **[表示] > [その他のウィンドウ] > [Python Environments (Python 環境)]** メニュー コマンドを選びます。
- ソリューション エクスプローラーでプロジェクトの **[Python 環境]** を右クリックし、**[すべての Python 環境の表示]** を選択します。

**[Python 環境]** ウィンドウを大きく広げると、これらのオプションがタブとして表示され、より操作しやすくなります。 わかりやすくするために、この記事ではタブが拡大表示されています。

![[Python Environments (Python 環境)] ウィンドウを広げた表示](media/environments-expanded-view.png)

## <a name="overview-tab"></a>[Overview (概要)] タブ

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
| (フォルダーとプログラムのリンク) | 環境のインストール フォルダー、python.exe インタープリター、pythonw.exe インタープリターに簡単にアクセスできます。 インストール フォルダーはエクスプローラーで開き、2 つのインタープリターはコンソール ウィンドウが開きます。 |

### <a name="startup-scripts"></a>スタートアップ スクリプト

日常のワークフローで対話型ウィンドウを使っていると、ヘルパー関数を作成して繰り返し使うことがあります。 たとえば、Excel でデータ フレームを開く関数を作成し、そのコードをスタートアップ スクリプトとして保存して、対話型ウィンドウでいつでも使えるようにするといった場合です。

スタートアップ スクリプトにはインポート、関数定義、その他文字どおりどのようなコードでも含めることができ、対話型ウィンドウは自動的にそれを読み込んで実行します。 このようなスクリプトは、2 つの方法で参照されます。

1. 環境をインストールすると、Visual Studio は `Documents\Visual Studio 2017\Python Scripts\<environment>` フォルダーを作成します。&lt;environment&gt; は、環境の名前と同じです。 **[対話型のスクリプトを確認する]** コマンドを使って、環境固有のフォルダーに簡単に移動できます。 その環境の対話型ウィンドウを開始すると、このフォルダーで見つかったすべての `.py` ファイルがアルファベット順に読み込まれて実行されます。

1. **[ツール] > [オプション] > [Python ツール] > [対話型ウィンドウ]** タブ (「[対話型ウィンドウ オプション](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)」を参照) の**[スクリプト]** コントロールでは、すべての環境で読み込まれて実行されるスタートアップ スクリプトの追加フォルダーを指定します。 ただし、この機能は現時点では機能しません。

## <a name="configure-tab"></a>[Configure (構成)] タブ

次の表で説明するような詳細が表示されます。 このタブが存在しない場合は、Visual Studio がすべての詳細情報を自動的に管理していることを意味します。

![[Python Environments (Python 環境)] の [Configure (構成)] タブ](media/environments-configure-tab.png)

| フィールド | 説明 |
| --- | --- |
| **説明** | 環境の名前です。 |
| **Prefix path (プレフィックスのパス)** | インタープリターの基本フォルダーの場所です。 この値を入力して **[自動検出]** をクリックすると、Visual Studio が他のフィールドを設定します。 |
| **Interpreter Path (インタープリターのパス)** | インタープリターの実行可能ファイルへのパスです。通常は、プレフィックスのパスの後に `python.exe` を付けたものです。 |
| **Windowed interpreter (ウィンドウ形式のインタープリター)** | コンソールではない実行可能ファイルへのパスです。多くの場合、プレフィックスのパスの後に `pythonw.exe` を付けたものです。 |
| **Library path (ライブラリのパス)**<br/>(使用可能な場合) | 標準ライブラリのルートを指定します。ただし、Visual Studio がさらに正確なパスをインタープリターに要求できる場合、この値は無視される可能性があります。 |
| **Language version (言語バージョン)** | ドロップダウン メニューから選びます。 |
| **アーキテクチャ** | 通常は自動的に検出されて設定されます。されない場合は 32 ビットまたは 64 ビットを指定します。 |
| **Path environment variable (パス環境変数)** | 検索パスを探すためにインタープリターが使う環境変数です。 Visual Studio は、Python を開始するとき、プロジェクトの検索パスが含まれるように変数の値を変更します。 通常、このプロパティは `PYTHONPATH` に設定する必要がありますが、一部のインタープリターでは別の値が使われます。 |

## <a name="packages-tab"></a>[パッケージ] タブ

*旧バージョンでは "pip" も表示されます。*

環境にインストールされているパッケージを管理します。それにより、ユーザーは新しいパッケージ (すべての依存関係を含む) の検索とインストールもできるようになります。

既にインストールされているパッケージには、パッケージを更新するためのコントロール (上向き矢印) とアンインストールするためのコントロール (円内の X) が表示されます。

![[Python 環境] の [パッケージ] タブ](media/environments-pip-tab-controls.png)

検索用語を入力すると、インストール済みのパッケージと PyPI からインストールできるパッケージの一覧がフィルター処理されます。

!["num" で検索を実行中の [Python 環境] の [パッケージ] タブ](media/environments-pip-tab.png)

検索ボックスに、`pip install` コマンドと `--user` や `--no-deps` などのフラグを直接入力することもできます。

パッケージをインストールすると、ファイル システム上の環境の `Lib` フォルダー内にサブフォルダーが作成されます。 たとえば、Python 3.6 を `c:\Python36` にインストールすると、パッケージは `c:\Python36\Lib` にインストールされます。Anaconda3 を `c:\Program Files\Anaconda3` にインストールすると、パッケージは `c:\Program Files\Anaconda3\Lib` にインストールされます。

後者の場合、ファイル システムの保護された領域 `c:\Program Files` に環境があるため、Visual Studio は、パッケージ サブフォルダーを作成できるように、管理者特権で `pip install` を実行する必要があります。 管理者特権への昇格が必要な場合、Visual Studio により "この環境でパッケージのインストール、更新、削除を行うには、管理者特権が必要な場合があります" というプロンプトが表示されます。

![パッケージ インストールのための昇格時のプロンプト](media/environments-pip-elevate.png)

**[今すぐ昇格]** を選ぶと、1 回の操作について pip に管理者特権が付与され、アクセス許可を求めるオペレーティング システムのプロンプトも対象になります。 **[管理者特権なしで続行]** を選ぶと、パッケージのインストールは試みられますが、pip がフォルダーを作成しようとすると、"エラー: 'C:\Program Files\Anaconda3\Lib\site-packages\png.py' を作成できませんでした: アクセス許可が拒否されました" のような出力で失敗します。

**[パッケージのインストール時か削除時に必ず昇格]** を選ぶと、対象の環境ではダイアログが表示されなくなります。 再びダイアログが表示されるようにするには、**[ツール] > [オプション] > [Python ツール] > [全般]** に移動し、**[永続的に表示されないすべてのダイアログをリセットする]** ボタンを選びます。

同じオプション タブでは、**[常に管理者として pip を実行する]** を選んで、すべての環境でダイアログを非表示にすることもできます。 「[Options - General tab](python-support-options-and-settings-in-visual-studio.md#general-options)」([全般] タブのオプション) をご覧ください。

## <a name="intellisense-tab"></a>[IntelliSense] タブ

IntelliSense 入力候補データベースの現在の状態を示します。

![[Python Environments (Python 環境)] の [IntelliSense] タブ](media/environments-intellisense-tab.png)

**Visual Studio 2017 バージョン 15.5** 以前は、IntelliSense による補完は、そのライブラリ用にコンパイルされているデータベースに依存しています。 データベースの構築はライブラリのインストール時にバックグラウンドで実行されますが、時間がかかる可能性があり、コードの記述の開始時には完了していないことがあります。 **Visual Studio 2017 バージョン 15.6** 以降は、特に有効にすることを選択しない限り、データベースに依存しないで完了する高速な方法が使用されます。

Visual Studio は新しい環境を検出すると (またはユーザーが追加すると)、ライブラリのソース ファイルを分析することで、データベースのコンパイルを自動的に開始します。 インストールされている内容により、この処理には 1 分から 1 時間以上かかることがあります (たとえば、Anaconda には多くのライブラリが付属しており、データベースのコンパイルに少し時間がかかります)。完了すると、詳細な IntelliSense が提供され、新しいライブラリをインストールするまでデータベースを再度更新する (**[Refresh DB]\(DB の更新\)** ボタンで) 必要はありません。

データがコンパイルされていないライブラリには、**!** が表示されます。環境のデータベースが完成していない場合は、**!** も メイン環境リストのライブラリの横に表示されます。

## <a name="see-also"></a>関連項目

- [Visual Studio での Python 環境の管理](managing-python-environments-in-visual-studio.md)
- [プロジェクトのインタープリターの選択](selecting-a-python-environment-for-a-project.md)
- [依存関係の requirements.txt の使用](managing-required-packages-with-requirements-txt.md)
- [検索パス](search-paths.md)
