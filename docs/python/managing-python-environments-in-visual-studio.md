---
title: Python 環境とインタープリターを管理する
description: '[Python 環境] ウィンドウを使用して、グローバル環境、仮想環境、および conda 環境を管理し、Python インタープリターとパッケージをインストールし、環境を Visual Studio プロジェクトに割り当てます。'
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: fbefd6a09537227f9b2343d2311dd1e68b9f0a23
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio で Python 環境を作成および管理する方法

Python *環境*は、その中で Python コードを実行するコンテキストであり、グローバル環境、仮想環境、および conda 環境が含まれます。 1 つの環境は、インタープリター、ライブラリ (通常は Python 標準ライブラリ)、およびインストールされているパッケージのセットで構成されます。 これらのコンポーネントがすべて合わさって、有効な言語の構造と構文、アクセスできるオペレーティング システム機能、使用できるパッケージが決まります。

Windows の Visual Studio では、この記事で説明する [[Python 環境]](#the-python-environments-window) ウィンドウで、これらの環境を管理し、新しいプロジェクトの既定値として 1 つの環境を選択します。 特定のプロジェクトに対して、既定ではなく、特定の環境を選択することもできます。

**注**: Visual Studio で Python を初めて使用される場合は、次の記事で必要な予備知識についてご確認ください。

- [Visual Studio での Python の使用](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio での Python サポートのインストール](installing-python-support-in-visual-studio.md)

**[ファイル]** > **[開く]** > **[フォルダー]** コマンドを使用してフォルダーとしてのみ開かれた Python コードの環境は管理できないことにも注意してください。 Visual Studio の環境機能を使用するには、[既存のコードから Python プロジェクトを作成](quickstart-01-python-in-visual-studio-project-from-existing-code.md)します。

環境にパッケージをインストールする場合は、[[パッケージ] タブ](python-environments-window-tab-reference.md#packages-tab)を参照してください。

## <a name="types-of-environments"></a>環境の種類

### <a name="global-environments"></a>グローバル環境

各 Python インストール(Python 2.7、Python 3.6、Anaconda 4.4.0 など。「[Python インタープリターの選択とインストール](installing-python-interpreters.md)」を参照) で、独自のグローバル環境が保持されます。 各環境は、特定の Python インタープリター、その標準ライブラリ、および事前インストールされたパッケージのセットで構成されます。 グローバル環境にパッケージをインストールすると、グローバル環境を使用するすべてのプロジェクトでパッケージが使用できるようになります。 グローバル環境がファイル システムの保護領域にある場合 (`c:\program files` など)、パッケージをインストールするには管理者特権が必要です。

グローバル環境は、コンピューター上のすべてのプロジェクトで使用できます。 Visual Studio では、1 つのグローバル環境を既定の環境として選択します。プロジェクトに対して別の環境を特に選ばない限り、すべてのプロジェクトでこれが使用されます。 詳細については、「[プロジェクト用の環境の選択](selecting-a-python-environment-for-a-project.md)」をご覧ください。

### <a name="virtual-environments"></a>仮想環境

グローバル環境にインストールされたパッケージは、グローバル環境を使うすべてのプロジェクトで使用できるため、2 つのプロジェクトで、互換性のないパッケージや同じパッケージの異なるバージョンが必要な場合、競合が発生する可能性があります。 仮想環境では、このような競合を避けるために、グローバル環境のインタープリターと標準ライブラリを使用しながら、分離フォルダーで独自のパッケージ ストアを保持します。

Visual Studio では、特定のプロジェクト用の仮想環境を作成可能で、これはプロジェクトのサブフォルダーに格納されます。 Visual Studio には、仮想環境から `requirements.txt` ファイルを生成し、他のコンピューターで環境を簡単に再作成するためのコマンドが用意されています。 詳細については、[仮想環境の使用](selecting-a-python-environment-for-a-project.md#using-virtual-environments)に関するページをご覧ください。

### <a name="conda-environments"></a>conda 環境

conda 環境は `conda` ツールを使用して作成される環境です。Visual Studio 2017 バージョン 15.7 以降では、統合 conda 管理が使用されます  (Anaconda または Miniconda が必要です。Anaconda は Visual Studio インストーラーを通して利用できるようになります。[インストール - Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017) に関するページを参照してください)。

> [!Note]
> conda 環境で最適な結果を得るためには、conda 4.4.8 以降 (conda バージョンは Anaconda バージョンとは異なります) をご使用ください。 Visual Studio 2017 インストーラーから Anaconda 5.1 をインストールする

conda 環境が格納されている conda バージョンや、その他の情報を参照するには、Anaconda コマンド プロンプト (つまり、Anaconda がパス内に存在するコマンド プロンプト) で `conda info` を実行します。

```bash
conda info
```
conda 環境フォルダーは次のように表示されます。

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

conda 環境はプロジェクトと共に格納されないことから、グローバル環境と同じように機能します。 たとえば、conda 環境に新しいパッケージをインストールすると、その環境を使用するすべてのプロジェクトでパッケージが使用できるようになります。

Visual Studio 2017 バージョン 15.6 以前の場合、conda 環境は、「[既存の環境を手動で識別する](#manually-identify-an-existing-environment)」に記載の説明に従って手動でポイントすることにより使用できます。

Visual Studio 2017 バージョン 15.7 以降では、次のセクションに説明するように、conda 環境が自動的に検出され、**[Python 環境]** ウィンドウに表示されます。

## <a name="the-python-environments-window"></a>[Python 環境] ウィンドウ

Visual Studio が認識した環境が **[Python 環境]** ウィンドウに表示されます。 このウィンドウを開くには、次のいずれかの方法を使用します。

- **[表示]** > **[その他のウィンドウ]** > **[Python 環境]** メニュー コマンドを選びます。
- ソリューション エクスプローラーでプロジェクトの **[Python 環境]** ノードを右クリックし、**[すべての Python 環境の表示]** を選択します。

    ![ソリューション エクスプローラーの [View All Python Environments (すべての Python 環境の表示)] コマンド](media/environments-view-all.png)

いずれの場合も、**[Python 環境]** ウィンドウはソリューション エクスプローラーの兄弟タブとして表示されます。

![[Python Environments (Python 環境)] ウィンドウ](media/environments-default-view.png)

太字で表示される既定の環境は Python 3.6 で、Visual Studio では新しいプロジェクトに対してこれを使用します。 リストされている環境はいずれも (種類に関係なく) 既定値として使用することができます。

ウィンドウの下部に表示されるコマンドは、選択されたインタープリターに適用されます。これは `C:\Python36-32` の固有のインストールです (太字で表示された既定の環境は Anaconda インストールの一部です)。 想定した環境が見つからない場合は、「[既存の環境を手動で識別する](#manually-identify-an-existing-environment)」を参照してください。

表示されている各環境の右側に、その環境の対話型のウィンドウを開くコントロールがあります。 (Visual Studio 2017 15.5 以前のバージョンでは、環境の IntelliSense データベースを更新する別のコントロールが表示されます。 データベースの詳細については、[環境ウィンドウ リファレンス](python-environments-window-tab-reference.md#intellisense-tab)に関するページを参照してください)。

環境の一覧の下には、[[Python 環境] ウィンドウ タブ リファレンス](python-environments-window-tab-reference.md)に説明がある **[概要]**、**[パッケージ]**、および **[IntelliSense]** の各オプション用のドロップダウン セレクターが表示されます。 また、**[Python 環境]** ウィンドウを大きく広げると、これらのオプションがタブとして表示され、より操作しやすくなります。

![[Python Environments (Python 環境)] ウィンドウを広げた表示](media/environments-expanded-view.png)

上図には、この特定のコンピューター上に存在する環境の完全なリストに加えて、環境を作成するための追加のコマンドも表示されています。

> [!Note]
> Visual Studio はシステム サイト パッケージのオプションを尊重しますが、Visual Studio 内からそれを変更する方法は用意されていません。

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | Visual Studio での Python 環境については、[こちらのビデオ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) をご覧ください (2 分 35 秒)。|

### <a name="what-if-no-environments-appear"></a>環境が表示されない場合

環境が表示されない場合は、Visual Studio が標準的な場所で Python インストールを検出できなかったことを意味します。 たとえば、Visual Studio 2017 をインストールしたが、Python ワークロードのインストーラー オプションですべてのインタープリター オプションを選択解除している場合があります。 同様に、Visual Studio 2015 以前をインストールしているが、インタープリターを手動でインストールしなかった場合があります ([Python インタープリターのインストール](installing-python-interpreters.md)に関する記事を参照してください)。

コンピューターに Python インタープリターがあることがわかっているが、Visual Studio で検出されない場合は、**[+ カスタム]** コマンドを使用して、その場所を手動で指定します。 次のセクション「[既存の環境を手動で識別する](#manually-identify-an-existing-environment)」を参照してください。

> [!Tip]
> python.org からのインストーラーを使用することによる Python 2.7.11 から Python 2.7.14 へのアップグレードなど、既存のインタープリターに対する更新プログラムを検出します。インストール プロセス中に、古くなった環境が **Python 環境**の一覧から消え、その場所に更新プログラムが表示されます。
>
> ただし、ファイル システムを使用してインタープリターとその環境を手動で移動している場合、Visual Studio は新しい場所がわかりません。 詳細については、「[、インタープリターを移動する](installing-python-interpreters.md#moving-an-interpreter)」を参照してください。

<a name="manually-identifying-an-existing-environment></a>

## <a name="manually-identify-an-existing-environment"></a>既存の環境を手動で識別する

標準と異なる場所にインストールされている環境 (Visual Studio 2017 バージョン 15.6 以前の conda 環境など) を識別するには、次の手順を使用します。

1. **[Python 環境]** ウィンドウで **[+ カスタム]** を選択します。**[構成]** タブが開きます。

    ![新しいカスタム環境の既定のビュー](media/environments-custom-1.png)

1. **[Description (説明)]** フィールドに環境の名前を入力します。

1. **[プレフィックス パス]** フィールドで、インタープリターのパスを入力するか参照します (**...*** を使用します)。

1. Visual Studio がその場所 (次の図に示した conda 環境用のパスなど) で Python インタープリターを検出した場合は、**[自動検出]** コマンドが有効になります。 **[自動検出]* コマンドを選択すると、残りのフィールドが入力されます。 これらのフィールドは、手動で入力することもできます。

    ![[自動検出] コマンドの有効化](media/environments-custom-2.png)

    ![[自動検出] 使用後の環境フィールドの入力](media/environments-custom-3.png)

1. フィールドに目的の値が入力されたら、**[適用]** を選択して構成を保存します。 これで、他の環境と同じように、Visual Studio 内で使用できます。

1. 手動で識別した環境を削除する必要がある場合は、**[構成]** タブの **[削除]** コマンドを選択します。自動検出された環境ではこのオプションは提供されません。 詳細については、「[タブを構成する](python-environments-window-tab-reference.md#configure-tab)」を参照してください。

## <a name="create-a-conda-environment"></a>conda 環境の作成

*Visual Studio 2017 バージョン 15.7 以降。*

1. **[Python 環境]** ウィンドウの **[+ conda 環境の作成]** を選択します。これにより、**[新しい conda 環境の作成]** タブが開きます。

    ![新しい conda 環境のためのタブを作成する](media/environments-conda-1.png)

1. **[名前]** フィールドに環境の名前を入力し、**[Python]** フィールドで基本的な Python インタープリターを選択し、**[作成]** を選択します。

1. **[出力]** ウィンドウに新しい環境の進捗状況が表示され、環境が作成されると CLI に関する指示がいくつか表示されます。

    ![conda 環境の正常な作成](media/environments-conda-2.png)

1. Visual Studio 内では、[プロジェクト用の環境の選択](selecting-a-python-environment-for-a-project.md)に関するページの説明に従って、他の環境の場合と同様に conda 環境をアクティブにすることができます。

1. 環境にパッケージをインストールするには、[[パッケージ] タブ](python-environments-window-tab-reference.md#packages-tab)を使用します。

## <a name="see-also"></a>関連項目

- [Python インタープリターのインストール](installing-python-interpreters.md)
- [プロジェクトのインタープリターの選択](selecting-a-python-environment-for-a-project.md)
- [依存関係の requirements.txt の使用](managing-required-packages-with-requirements-txt.md)
- [検索パス](search-paths.md)
- [[Python 環境] ウィンドウ リファレンス](python-environments-window-tab-reference.md)