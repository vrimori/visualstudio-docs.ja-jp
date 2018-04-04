---
title: Visual Studio での Python サポートのインストール | Microsoft Docs
description: Visual Studio 2017、2015、2013、2012、2010 で Python Tools for Visual Studio (PTVS) をインストールする方法の詳細と、オプションやインストールの場所について説明します。
ms.custom: ''
ms.date: 02/15/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 8a6bf78c0f0abcef9158bfdb753f5c8ea4050c33
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Windows に Visual Studio の Python サポートをインストールする

Visual Studio 用の Python サポート (Python Tools for Visual Studio (PTVS) とも言われます) をインストールするには、使用している Visual Studio のバージョンと一致するセクションの手順を実行します。

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 以前](#visual-studio-2013-and-earlier)

Visual Studio 2015 以前では、任意の [Python インタープリターをインストールする](installing-python-interpreters.md)必要があります (Python 3.5 およびそれ以前と 3.6 はサポート対象外のため、"Python バージョン 3.6 はサポートされていません" のようなメッセージが表示されます)。 同じページには、Visual Studio 2017 に既存の Python インタープリターを追加する手順もあります。

インストール手順を実行した後、Python サポートを簡単にテストするには、Alt + I キーを押して Python の対話型ウィンドウを開き、`2+2` を入力します。 `4` という出力が表示されない場合は、手順を再確認してください。

> [!Tip]
> Python ワークロードには、テンプレートの検出、テンプレート オプションの入力、およびプロジェクトとファイルの作成を行うためのグラフィカル ユーザー インターフェイスを提供する、有用な Cookiecutter 拡張機能が含まれています。 詳細については、「[Cookiecutter 拡張機能の使用](using-python-cookiecutter-templates.md)」を参照してください。

> [!Note]
> 現在、Python のサポートは Visual Studio for Mac では使用できませんが、Visual Studio Code によって Mac と Linux でも使うことができます。 「[questions and answers (質問と回答)](overview-of-python-tools-for-visual-studio.md#questions-and-answers)」をご覧ください。

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. 最新の Visual Studio 2017 インストーラーをダウンロードし、実行します。 Visual Studio が既にインストールされている場合は、Visual Studio インストーラーを実行し、**[変更]** オプションを選択して ([Visual Studio の変更](../install/modify-visual-studio.md)に関するページをご覧ください)、手順 2 へ進みます。

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 のインストールに関するコミュニティ</a>

    >[!Tip]
    > このコミュニティ版は、個人の開発者、クラス学習、学術研究、オープン ソース開発向けです。 その他の用途には、<a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> または <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a> を使用してください。

1. インストーラーによって、ワークロード一覧が表示されます。これは、特定の開発分野の関連オプションのグループです。 Python の場合、**[Python 開発]** ワークロードを選択します。

    ![Visual Studio インストーラーの [Python 開発] ワークロード](media/installation-python-workload.png)

    省略可能: データ サイエンスを扱っている場合、**[データ サイエンスと分析のアプリケーション]** ワークロードも検討してください。 このワークロードでは、Python だけでなく、R と F# 言語もサポートしています。 詳細については、「[データ サイエンスと分析のアプリケーション](../rtvs/data-science-and-analytical-applications-workload.md)」を参照してください。

    > [!Note]
    > Python とデータ サイエンスのワークロードは、Visual Studio 2017 バージョン 15.2 以降でのみ利用可能です。

1. インストーラーの右側から、必要に応じて追加のオプションを選択します。 既定のオプションを使用する場合は、この手順を省略します。

    ![Visual Studio インストーラーの [Python 開発] のオプション](media/installation-python-options.png)

    | オプション | 説明 |
    | --- | --- |
    | Python ディストリビューション | 使用する予定の Python 2、Python 3、Anaconda2、および Anaconda3 ディストリビューションの 32 ビットおよび 64 ビットのバリアントを任意の組み合わせで選択します。 それぞれには、ディストリビューションのインタープリター、ランタイム、およびライブラリが含まれます。 Anaconda とは、具体的には、さまざまな事前インストール パッケージを含むオープンなデータ サイエンス プラットフォームです。 (ディストリビューションを追加または削除する場合には、Visual Studio インストーラーへはいつでも戻ることができます。)**注**: Visual Studio インストーラー以外で配布をインストールした場合、ここで対応するオプションを確認する必要はありません。 Visual Studio は、既存の Python インストールを自動的に検出します。 [Python 環境](managing-python-environments-in-visual-studio.md)に関するページを参照してください。 |
    | cookiecutter テンプレートのサポート | テンプレートの検出、テンプレート オプションの入力、プロジェクトとファイルの作成を行うための Cookiecutter グラフィカル UI をインストールできます。 「[Cookiecutter 拡張機能の使用](using-python-cookiecutter-templates.md)」をご覧ください。 |
    | Python Web サポート | HTML、CSS、および JavaScript の編集をサポートする Web 開発用ツールを、Bottle、Flask、および Django フレームワークを使用するプロジェクトのテンプレートと共にインストールします。 「[Python Web プロジェクト テンプレート](python-web-application-project-templates.md)」を参照してください。 |
    | Python IoT サポート | Python を使用した、Windows IoT Core 開発がサポートされます。 |
    | Python ネイティブ開発ツール | Python のネイティブ拡張機能の開発するために必要な C++ コンパイラおよびその他のコンポーネントがインストールされます。 「[Python 用 C++ 拡張機能の作成](working-with-c-cpp-python-in-visual-studio.md)」を参照してください。 C++ を完全にサポートするには、**C++ によるデスクトップ開発**ワークロードもインストールします。 |
    | Azure Cloud Services コア ツール | Python での Azure Cloud Services で開発者に追加のサポートを提供します。 「[Azure クラウド サービス プロジェクト](python-azure-cloud-service-project-template.md)」を参照してください。 |

1. インストール後、Visual Studio を変更、起動、修復またはアンインストールするオプションが提供されます。 Visual Studio にインストールされているコンポーネントの更新プログラムが利用可能になると、**[変更]** ボタンは **[更新]** に変わります。 (その後、[変更] オプションは、ドロップダウン メニューから利用可能になります)。Windows の [スタート] メニューで "Visual Studio" を検索して、Visual Studio とインストーラーを起動することも可能です。

    ![インストーラーからの Visual Studio の起動、変更、またはアンインストール](media/installation-vs-launch.png)

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | Visual Studio での Python サポートのインストールについては、[こちらのビデオ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567) をご覧ください。|

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. **[コントロール パネル] の [プログラムと機能]** から Visual Studio インストーラーを実行し、**[Microsoft Visual Studio 2015]** を選択した後、**[変更]** を選択します。

1. インストーラーで、**[変更]** を選択します。

1. **[プログラミング言語] の [Python Tools for Visual Studio]** を選択し、**[次へ]** を選択します。

    ![Visual Studio 2015 インストーラーの PTVS オプション](media/installation-vs2015.png)

1. Visual Studio のセットアップが完了したら、[任意の Python インタープリターをインストールします](installing-python-interpreters.md)。 インタープリターは既にインストールされているが、Visual Studio によって自動的に検出されない場合は、「[既存の環境を手動で識別する](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)」を参照してください。

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 以前

1. 使用している Visual Studio のバージョンに適した Python Tools for Visual Studio のバージョンをインストールします。

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2)。 このプロセスのショートカットが、Visual Studio 2013 の **[ファイル] メニューの [新しいプロジェクト]** ダイアログにあります。
    - Visual Studio 2012: [PTVS 2.1 for Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 for Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [任意の Python インタープリターをインストールします](installing-python-interpreters.md)。 インタープリターは既にインストールされているが、Visual Studio によって自動的に検出されない場合は、「[既存の環境を手動で識別する](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)」を参照してください。

## <a name="install-locations"></a>インストールする場所

既定では、Python サポートは、コンピューター上のすべてのユーザーに対してインストールされます。

Visual Studio 2017 では、Python ワークロードは、`%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` にインストールされます。&lt;VS_edition&gt; は、Community、Professional、または Enterprise です。

Visual Studio 2015 以前のインストール パスを次に示します。

- 32 ビット:
  - パス: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - パスのレジストリの場所: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 ビット:
  - パス: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - パスのレジストリの場所: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

それぞれの文字について以下に説明します。

- &lt;VS_ver&gt; は、次のようになります。
  - Visual Studio 2015 では 14.0
  - Visual Studio 2013 では 12.0
  - Visual Studio 2012 では 11.0
  - Visual Studio 2010 では 10.0
- &lt;PTVS_ver&gt; はバージョン番号です (2.2、2.1、2.0、1.5、1.1、1.0 など)。

### <a name="user-specific-installations-15-and-earlier"></a>ユーザー固有のインストール (1.5 以前)

Python Tools for Visual Studio 1.5 以前では、インストールは現在のユーザーのみに許可されます。この場合、インストール パスは `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` になります。&lt;VS_ver&gt; と &lt;PTVS_ver &gt; は上記で説明したものと同じです。

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
