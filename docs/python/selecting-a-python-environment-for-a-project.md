---
title: "プロジェクトの環境を選択する | Microsoft Docs"
description: "Visual Studio のソリューション エクスプローラーでは、既定の環境を無視して、指定されたプロジェクトに常に使用する特定の Python インタープリター (環境) を割り当てることができます。 また、仮想環境を作成し、管理することもできます。"
ms.custom: 
ms.date: 02/20/2018
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
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>プロジェクトで使用する Python インタープリターと環境を選択する

Python プロジェクトのすべてのコードは、特定の環境のコンテキスト内で実行されます。 また、Visual Studio では、デバッグ、インポートとメンバーの入力候補、構文チェック、環境を必要とするその他のタスクにもその環境を使用します。

Visual Studio のすべての新しい Python プロジェクトは、最初は既定のグローバル環境を使用するように構成されています。この環境は、ソリューション エクスプローラーの **[Python 環境]** ノードに表示されます。

![ソリューション エクスプローラーに表示される既定のグローバル Python 環境](media/environments-project.png)

プロジェクトには、仮想環境を含め、他の環境を使用することができます。 一度にアクティブ化できる環境は 1 つのみです。

## <a name="using-global-environments"></a>グローバル環境を使用する

プロジェクトに特定のグローバル環境 ([手動で指定](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)した conda 環境など) を使用するには、**[Python 環境]** ノードを右クリックし、**[Python 環境の追加/削除]** を選択します。表示された一覧から、目的の環境を選択します。

![[Add/Remove Python Environments (Python 環境の追加/削除)] ダイアログ](media/environments-add-remove.png)

**[OK]** を選択すると、選択したすべての環境が **[Python 環境]** ノードと表示されます。 現在アクティブな環境は太字で表示されます。

![ソリューション エクスプローラーに表示される複数の Python 環境](media/environments-project-multiple.png)

別の環境をアクティブ化するには、その環境を右クリックし、**[環境のアクティブ化]** を選択します。 この選択はプロジェクトに保存され、以降、そのプロジェクトを開くたびにその環境がアクティブになります。

**[Python 環境の追加/削除]** ダイアログですべてのオプションをオフにすると、Visual Studio ではグローバルな既定の環境がアクティブになります。

## <a name="using-virtual-environments"></a>仮想環境を使用する

仮想環境は、特定の Python インタープリターと、他のグローバル環境や conda 環境とは異なる特定のライブラリ セットの固有の組み合わせです。 一般的に、プロジェクトに特定のニーズがあり、そのニーズを満たすために他の環境を変更したくない場合に仮想環境を使用します。

プロジェクトに追加された仮想環境は **[Python Environments (Python 環境)]** ウィンドウに表示され、他の環境と同じように、アクティブ化してパッケージを管理できます。

仮想環境の欠点として、ハード コーディングされたファイル パスを含むため、他の開発用コンピューターとの間で簡単に共有や転送ができないことに注意してください。 ただし、プロジェクトを受け取った側が `requirements.txt` ファイルを使用すると簡単に環境を復元できます。 詳細については、「[Managing required packages with requirements.txt](managing-required-packages-with-requirements-txt.md)」(requirements.txt で必要なパッケージを管理する) を参照してください。

### <a name="activating-an-existing-virtual-environment"></a>既存の仮想環境をアクティブ化する

他の場所で既に仮想環境を作成している場合は、次のようにプロジェクトでその仮想環境をアクティブ化することができます。

1. ソリューション エクスプローラーで **[Python 環境]** を右クリックし、**[既存の仮想環境を追加]** を選択します。

1. **[参照]** ダイアログが表示されたら、仮想環境があるフォルダーに移動して選択し、**[OK]** を選択します。 Visual Studio でその環境内に `requirements.txt` ファイルが検出されると、それらのパッケージをインストールするかどうかが確認されます。

1. しばらくすると、ソリューション エクスプローラーの **[Python 環境]** ノードに仮想環境が表示されます。 既定では仮想環境はアクティブ化されないので、仮想環境を右クリックし、**[環境をアクティブ化する]** を選択します。

### <a name="creating-a-virtual-environment"></a>仮想環境の作成

次のように、Visual Studio から新しい仮想環境を直接作成できます。

1. ソリューション エクスプローラーで **[Python 環境]** を右クリックし、**[仮想環境を追加]** を選択します。次のダイアログ ボックスが表示されます。

    ![仮想環境の作成](media/environments-add-virtual-1.png)

1. **[仮想環境の場所]** フィールドで仮想環境のパスを指定します。 名前のみを指定した場合、現在のプロジェクト内の指定された名前のサブフォルダーに仮想環境が作成されます。

1. ベース インタープリターとして環境を選択し**[作成]** を選択します。 環境の構成と必要なパッケージのダウンロード中は進行状況バーが表示されます。 この時点で、仮想環境は、その環境が含まれているプロジェクトの **[Python 環境]**  ウィンドウに表示されます。

1. 既定では、仮想環境はアクティブ化されません。 プロジェクトで仮想環境をアクティブ化するには、プロジェクトを右クリックし、**[環境をアクティブ化する]** を選択します。

> [!Note]
> 場所のパスに既存の仮想環境を指定した場合、Visual Studio で自動的に (環境の `lib` ディレクトリ内にある `orig-prefix.txt` ファイルを使用して) ベース インタープリターが検出され、[作成] ボタンは **[追加]** に変わります。
>
> 仮想環境を追加する場合に `requirements.txt` ファイルが存在していると、**[仮想環境の追加]** ダイアログにパッケージを自動的にインストールするオプションが表示されるため、別のコンピューターに簡単に環境を再作成できます。
>
> ![requirements.txt で仮想環境を作成する](media/environments-requirements-txt.png)
>
> いずれの方法でも、**[既存の仮想環境を追加]** コマンドを使用した場合と同じ結果になります。

### <a name="remove-a-virtual-environment"></a>仮想環境を削除する

1. ソリューション エクスプローラーで仮想環境を右クリックし、**[クリア]** を選択します。

1. 仮想環境をクリアするか削除するかが確認されます。 **[クリア]** を選択すると、その環境はプロジェクトで使用できなくなりますが、ファイル システムには残ります。 **[削除]** を選択すると、プロジェクトから環境がクリアされ、ファイル システムからも削除されます。 ベース インタープリターは影響を受けません。

## <a name="viewing-installed-packages"></a>インストールされているパッケージを表示する

ソリューション エクスプローラーで、特定の環境のノードを展開すると、その環境にインストールされているパッケージがすぐに表示されます (つまり、環境がアクティブな場合にコード内でそれらのパッケージをインポートして使用できます)。

![ソリューション エクスプローラーでの環境の Python パッケージ](media/environments-installed-packages.png)

新しいパッケージをインストールするには、環境を右クリックし、**[Python パッケージのインストール]**  を選択して **[Python 環境]** ウィンドウの **[パッケージ]** タブに切り替えます。 検索用語 (通常はパッケージ名) を入力すると、一致するパッケージが Visual Studio に表示されます。

Visual Studio 内で、パッケージ (および依存関係) は [Python Package Index (PyPI)](https://pypi.python.org/pypi) からダウンロードされます。ここでパッケージを検索することもできます。 Visual Studio のステータス バーと出力ウィンドウには、インストールに関する情報が表示されます。 パッケージをアンインストールするには、パッケージを右クリックして **[Remove (削除)]** を選びます。

表示されるエントリは常に正確であるとは限らず、インストールとアンインストールが信頼できない場合、または使用できない場合がある点に注意してください。 Visual Studio は、使用可能な場合は pip パッケージ マネージャーを使い、必要な場合はダウンロードしてインストールします。 Visual Studio は、easy_install パッケージ マネージャーを使うこともできます。 コマンド ラインから `pip` または `easy_install` を使ってインストールされたパッケージも表示されます。

また、現在 Visual Studio では、`conda` を使用して conda 環境にパッケージをインストールする操作はサポートされていません。 代わりにコマンド ラインから `conda` を使用してください。

> [!Tip]
> pip がパッケージのインストールに失敗する一般的な状況は、パッケージの `*.pyd` ファイルにネイティブ コンポーネントのソース コードが含まれる場合です。 必要なバージョンの Visual Studio がインストールされていない場合、pip はこれらのコンポーネントをコンパイルできません。 このような状況では、"`error: Unable to find vcvarsall.bat`" というエラー メッセージが表示されます。 多くの場合、`easy_install` ではコンパイル済みのバイナリをダウンロードでき、Python の古いバージョンに適したコンパイラは [http://aka.ms/VCPython27](http://aka.ms/VCPython27) からダウンロードできます。 詳しくは、Python Tools チーム ブログの「[How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/)」("vcvarsallbat が見つからない" という問題への対処方法) をご覧ください。

## <a name="see-also"></a>関連項目

- [Visual Studio での Python 環境の管理](managing-python-environments-in-visual-studio.md)
- [依存関係の requirements.txt の使用](managing-required-packages-with-requirements-txt.md)
- [検索パス](search-paths.md)
- [[Python 環境] ウィンドウ リファレンス](python-environments-window-tab-reference.md)