---
title: "Visual Studio での Python のインストール | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
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
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: e0a51155a42fb51244114da86a292381a7a28a21
ms.lasthandoff: 03/27/2017

---

# <a name="installing-python-support-for-visual-studio"></a>Visual Studio 用の Python サポートのインストール

Visual Studio 用の Python サポートをインストールするには、使用している Visual Studio のバージョンと一致するセクションの手順を実行します。

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 以前](#visual-studio-2013-and-earlier)

Visual Studio 2015 以前では、任意の Python インタープリターをインストールする必要があります。 詳細については、「[Python Environments (Python 環境)](python-environments.md)」を参照してください。

インストール手順を実行した後、Python サポートを簡単にテストするには、Alt + I キーを押して Python の対話型ウィンドウを開き、`2+2` を入力します。 `4` という出力が表示されない場合は、手順を再確認してください。

> [!Tip]
> Python ワークロードには、テンプレートの検出、テンプレート オプションの入力、およびプロジェクトとファイルの作成を行うためのグラフィカル ユーザー インターフェイスを提供する、有用な Cookiecutter 拡張機能が含まれています。 詳細については、「[Using Cookiecutter (Cookiecutter の使用)](cookiecutter.md)」を参照してください。

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. ["Visual Studio 2017 Preview" を https://www.visualstudio.com/vs/preview から](https://www.visualstudio.com/vs/preview)インストールします。 **注:** この Preview チャネルは Visual Studio 2017 のリリース バージョンとは*異なり*、Python サポートなど、将来の Visual Studio 2017 更新プログラム用に開発中の機能が含まれます。

1. プレビュー インストーラーで、**[Web & Cloud (Web と クラウド)]、[Python 開発]** ワークロードの順に選択します。

    ![Visual Studio インストーラーの [Python 開発] ワークロード](media/installation-python-workload.png)

1. インストーラーの右側で、インストールに含める Python インタープリターとその他の関連ツールを選択します。 たとえば、Python の C++ 拡張機能を開発する場合は、**[Python ネイティブ開発ツール]** オプションを含めます。

    ![Visual Studio インストーラーの [Python 開発] のオプション](media/installation-python-options.png)

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. **[コントロール パネル] の [プログラムと機能]** から Visual Studio インストーラーを実行し、**[Microsoft Visual Studio 2015]** を選択した後、**[変更]** を選択します。

1. インストーラーで、**[変更]** を選択します。

1. **[プログラミング言語] の [Python Tools for Visual Studio]** を選択し、**[次へ]** を選択します。

    ![Visual Studio 2015 インストーラーの PTVS オプション](media/installation-vs2015.png)    

1. Visual Studio のセットアップが完了したら、[任意の Python インタープリターをインストールします](python-environments.md#selecting-and-installing-python-interpreters)。

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 以前

1. 使用している Visual Studio のバージョンに適した Python Tools for Visual Studio のバージョンをインストールします。

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2)。 このプロセスのショートカットが、Visual Studio 2013 の **[ファイル] メニューの [新しいプロジェクト]** ダイアログにあります。
    - Visual Studio 2012: [PTVS 2.1 for Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 for Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [任意の Python インタープリターをインストールします](python-environments.md#selecting-and-installing-python-interpreters)。

## <a name="install-locations"></a>インストールする場所

既定では、Python サポートは、コンピューター上のすべてのユーザーに対してインストールされます。

Visual Studio 2017 では、Python ワークロードは、`%ProgramFiles(x86)%\Microsoft Visual Studio\Preview\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` にインストールされます。&lt;VS_edition&gt; は、Community、Professional、または Enterprise です。

Visual Studio 2015 以前のインストール パスを次に示します。

- 32 ビット:
  - パス: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - パスのレジストリの場所: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 ビット:
  - パス: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - パスのレジストリの場所: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

ここで、

- &lt;VS_ver&gt; は、次のようになります。    
    - Visual Studio 2015 では 14.0
    - Visual Studio 2013 では 12.0
    - Visual Studio 2012 では 11.0
    - Visual Studio 2010 では 10.0
- &lt;PTVS_ver&gt; はバージョン番号です (2.2、2.1、2.0、1.5、1.1、1.0 など)。

### <a name="user-specific-installations-15-and-earlier"></a>ユーザー固有のインストール (1.5 以前)

Python Tools for Visual Studio 1.5 以前では、インストールは現在のユーザーのみに許可されます。この場合、インストール パスは `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` になります。&lt;VS_ver&gt; と &lt;PTVS_ver &gt; は上記で説明したものと同じです。

