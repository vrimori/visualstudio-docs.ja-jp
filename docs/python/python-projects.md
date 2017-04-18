---
title: "Visual Studio での Python プロジェクト | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9c53f76-d0ef-4095-8b39-b7eb9bb33aba
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
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: eb3abd0f37e52f2b1db3793a5471b74a5e0c37ff
ms.lasthandoff: 04/10/2017

---

# <a name="python-projects"></a>Python プロジェクト

通常、Python アプリケーションはフォルダーとファイルのみを使って定義されますが、アプリケーションが大きくなり、おそらく自動生成されたファイル、Web アプリケーション用 JavaScript などが含まれるようになると、複雑になる可能性があります。 このような複雑さを管理しやすくするには、Python アプリケーション用の Visual Studio プロジェクトを作成できます。 Python プロジェクト (`.pyproj` ファイル) には、プロジェクトに関連付けられたすべてのソース ファイルとコンテンツ ファイルの識別、各ファイルのビルド情報の格納、ソース管理システムと統合するための情報の保持、論理コンポーネントへのアプリケーションの整理の補助などの機能があります。

さらに、プロジェクトは常に Visual Studio の*ソリューション*内で管理され、ソリューションは相互に参照する可能性のある任意の数のプロジェクトを含むことができます。 たとえば、Python プロジェクトは拡張モジュール用に C++ プロジェクトを参照でき、それにより、Python プロジェクトのデバッグを開始するとき、Visual Studio は (必要な場合) C++ プロジェクトを自動的にビルドします (一般的な説明については、「[Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)」をご覧ください)。

![ソリューション エクスプローラーでの Python プロジェクト](media/projects-solution-explorer.png)

Visual Studio には、多数のアプリケーション構造を短時間で設定するためのさまざまな Python プロジェクト テンプレートが用意されており、既存のフォルダー ツリーからプロジェクトを作成するためのテンプレートや、クリーンな空のプロジェクトを作成するためのテンプレートなどがあります。 詳しくは、後の「[プロジェクト テンプレート](#project-templates)」をご覧ください。

このトピックの内容

- [ファイルの追加、スタートアップ ファイルの割り当て、環境の設定](#adding-files-assigning-a-startup-file-and-setting-environments)
- [プロジェクト テンプレート](#project-templates)
- [リンク ファイル](#linked-files)
- [参照](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> プロジェクトを使わなくても、Visual Studio で Python コードの作業を問題なく行うことができます。Python ファイル自体を開き、オート コンプリート、IntellSense、デバッグなどの機能を利用できます (エディターで右クリックし、**[デバッグの開始]/[デバッグなしで開始]** を選びます)。 ただし、このようなコードは常に既定のグローバル環境を使うので、コードが別の環境向けのものである場合は正しくない入力候補やエラーが表示されることがあります。 さらに、Visual Studio は 1 つのファイルが開かれたフォルダー内のすべてのファイルとパッケージを分析するので、かなりの CPU 時間を消費します。
>
> 後の「[既存ファイルからのプロジェクトの作成](#creating-a-project-from-existing-files)」で説明されているように、既存のコードから Visual Studio プロジェクトを作成すると簡単です。

Visual Studio での Python プロジェクトの概要については、「[Getting Started with Python Tools Part 2: Projects](https://youtu.be/KHPoVpL7zHg?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)」(Python Tools の概要パート 2: プロジェクト) (youtube.com、3 分 18 秒) をご覧ください。

> [!VIDEO https://www.youtube.com/embed/KHPoVpL7zHg]

また、「[Deep Dive: Using source control with Python projects](https://youtu.be/Aq8eqApnugM)」(Deep Dive: Python プロジェクトでのソース管理の使用) (youtube.com、8 分 55 秒) のビデオもご覧ください。

> [!VIDEO https://www.youtube.com/embed/Aq8eqApnugM]


## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>ファイルの追加、スタートアップ ファイルの割り当て、環境の設定

アプリケーションを開発するときは、通常、さまざまな種類の新しいファイルをプロジェクトに追加する必要があります。 プロジェクトを右クリックして **[追加] > [既存の項目...]** を選ぶと、簡単にファイルを参照して追加できます。また、**[追加] > [新しい項目...]** を選ぶと、空の Python ファイル、Python クラス、単体テスト、Web アプリケーション関連の各種ファイルを含むさまざまな項目テンプレートがダイアログに表示されます。 テスト プロジェクトでこれらのオプションを調べて、お使いのバージョンの Visual Studio で使用可能なものについて学習することをお勧めします。

Python の各プロジェクトには 1 つのスタートアップ ファイルが割り当てられており、ソリューション エクスプローラーでは太字で表示されます。 デバッグを開始するとき (F5 キーを押すか、**[デバッグ] > [デバッグを開始]** を選ぶ)、または対話型ウィンドウでプロジェクトを実行するとき (Shift + Alt + F5 キーを押すか、**[デバッグ] > [Execute Project in Python Interactive (Python Interactive でプロジェクトを実行)]** を選ぶ) は、このファイルを実行します。 これを変更するには、新しいファイルを右クリックし、**[Set as Startup File (スタートアップ ファイルとして設定)]** を選びます。

> [!Tip]
> プロジェクトから選択したスタートアップ ファイルを削除し、新しいスタートアップ ファイルを選択しないと、プロジェクトを実行しようとしたときに、Python 出力ウィンドウが表示されてもほとんど瞬時に消えます。 このような動作が発生する場合は、スタートアップ ファイルを割り当ててあることを確認します。 また、このような場合に出力ウィンドウを開いたままにするには、プロジェクトを右クリックし、**[プロパティ]** の **[デバッグ]** タブを選び、**[インタープリター引数]** フィールドに `-i` を追加します。 このようにすると、プログラム完了後にインタープリターは対話モードになり、ユーザーが Ctrl + Z キー、Enter キーの順に押して終了するまで、ウィンドウは開いたままになります。

新しいプロジェクトは常に既定のグローバル Python 環境と関連付けられます。 プロジェクトを別の環境 (仮想環境を含む) と関連付けるには、プロジェクトで **[Python Environments (Python 環境)]** ノードを右クリックし、**[Add/Remove Python Environments (Python 環境の追加/削除)]** を選んで、使う環境を選びます。 アクティブな環境を変更するには、目的の環境を右クリックして **[Activate Environment (環境のアクティブ化)]** を選びます (次の図を参照)。 詳しくは、「[Python 環境](python-environments.md#project-specific-environments)」をご覧ください。

![Python プロジェクト用の環境のアクティブ化](media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>プロジェクト テンプレート

Visual Studio には、新規に、または既存のコードから、Python プロジェクトをセットアップする複数の方法が用意されています。 テンプレートを使うには、**[ファイル] > [新規] > [プロジェクト]** メニュー コマンドを選ぶか、ソリューション エクスプローラーでソリューションを右クリックして **[追加] > [新しいプロジェクト...]** を選びます。どちらの場合も、**[新しいプロジェクト]** ダイアログが表示されます。 Python 固有のテンプレートを表示するには、「Python」を検索するか、**[テンプレート] > [他の言語] > [Python]** ノードを選びます。

![Python テンプレートが表示されている [新しいプロジェクト] ダイアログ](media/projects-new-project-dialog.png)

次の表は、Visual Studio 2017 で使うことができるテンプレートをまとめたものです (以前のバージョンでは利用できないテンプレートもあります)。

| テンプレート | 説明 | 
| --- | --- |
| [From Existing Python Code (既存の Python コードから)](#creating-a-project-from-existing-files) | フォルダー構造に存在する既存の Python コードから Visual Studio プロジェクトを作成します。  |
| Python Application (Python アプリケーション) | 空のソース ファイルを 1 つ含む新しい Python アプリケーションの基本的なプロジェクト構造です。 既定では、プロジェクトは既定のグローバル環境のコンソール インタープリターで実行します。これは、[異なる環境を割り当てる](python-environments.md#project-specific-environments)ことで変更できます。 |
| [Azure クラウド サービス](template-azure-cloud-service.md) | Python で記述された Azure クラウド サービス用のプロジェクトです。 |
| [Web プロジェクト](template-web.md) | Bottle、Django、Flask、Flask/Jade などのさまざまなフレームワークに基づく Web サーバー用のプロジェクトです。 |
| IronPython Application (IronPython アプリケーション) | [Python Application (Python アプリケーション)] テンプレートに似ていますが、IronPython を既定で使って、.NET 相互運用と .NET 言語での混合モード デバッグを可能にします。 |
| IronPython WPF Application (IronPython WPF アプリケーション) | IronPython と、アプリケーションのユーザー インターフェイス用に Windows Presentation Foundation の XAML ファイルを使うプロジェクト構造です。 Visual Studio は XAML UI デザイナーを提供し、コードビハインドを Python で記述でき、アプリケーションはコンソールを表示しないで実行します。 |
| IronPython Silverlight Web Page (IronPython Silverlight Web ページ) | Silverlight を使ってブラウザーで実行する IronPython プロジェクトです。 アプリケーションの Python コードは、スクリプトとして Web ページに含まれます。 定型のスクリプト タグは、Silverlight の内部で実行する IronPython を初期化する JavaScript コードを生成し、それによって Python コードは DOM と対話できます。 |
| IronPython Windows Forms Application (IronPython Windows フォーム アプリケーション) | IronPython と、Windows フォームを含むコードを使って作成された UI を使うプロジェクト構造。 アプリケーションはコンソールを表示しないで実行します。 |
| Background Application (IoT) (バックグラウンド アプリケーション (IoT)) | デバイス上でバックグラウンド サービスとして実行する Python プロジェクトの配置をサポートします。 詳しくは、[Windows IoT デベロッパー センター](https://dev.windows.com/en-us/iot)をご覧ください。 |
| Python 拡張機能モジュール | このテンプレートは、Visual Studio 2017 Preview の Python ワークロードで **Python ネイティブ開発ツール**をインストールしてある場合、Visual C++ の下に表示されます (「[インストール](installation.md)」を参照)。 「[Python 向け C++ 拡張機能の作成](cpp-and-python.md)」で説明されているものに似た、C++ 拡張 DLL のコア構造を提供します。 |

<a name="create-project-from-existing-files"</a>
### <a name="creating-a-project-from-existing-files"></a>既存ファイルからのプロジェクトの作成

1. **[ファイル] > [新規] > [プロジェクト...]** メニューを選び、**[From Existing Python Code (既存の Python コードから)]** テンプレートを選びます。
1. 次のダイアログ ボックスで、既存のコードへのパス、ファイルの種類のフィルター、プロジェクトで必要な検索パスを設定し、**[次へ]** を選びます。

    ![[既存のコードから新しいプロジェクトを作成]、手順 1](media/projects-from-existing-1.png)

1. プロジェクトとスタートアップ ファイルの環境を選び、**[次へ]** を選びます (ダイアログにはフォルダー ツリーのルートにあるファイルしか表示されないことに注意してください。目的のファイルがサブフォルダーにある場合は、スタートアップ ファイルを空白のままにし、ソリューション エクスプローラーを使って後で設定します)。

    ![[既存のコードから新しいプロジェクトを作成]、手順 2](media/projects-from-existing-2.png)

1. プロジェクト ファイルを保存する場所を選びます (これにより元のソース ファイルが移動またはコピーされることはないので、コピーが必要な場合は、テンプレートを使う前に行う必要があります)。 このダイアログでは、仮想環境の自動検出を組み込み、異なる Web フレームワーク用にプロジェクトをカスタマイズすることもできます。

    ![[既存のコードから新しいプロジェクトを作成]、手順 3](media/projects-from-existing-3.png)

1.  **[完了]** を選ぶと、プロジェクトが作成されて、ソリューション エクスプローラーで開かれます。 .pyproj ファイルを別の場所に移動したい場合は、ソリューション エクスプローラーでファイルを選び、**[ファイル] > [名前を付けて保存]** を選びます。 プロジェクト内のファイル参照は更新されますが、コード ファイルは移動されません。

## <a name="linked-files"></a>リンク ファイル

リンク ファイルは、プロジェクトに取り込まれますが、通常はアプリケーションのプロジェクト フォルダーの外部に存在するファイルです。 ソリューション エクスプローラーでは、通常のファイルにショートカットがオーバーレイされたアイコンで示されます。 ![リンク ファイルのアイコン](media/projects-linked-file-icon.png)

リンク ファイルは、通常の `<Compile Include="...">` 要素を使って `.pyproj` ファイルで指定されます。 ディレクトリ構造の外部の相対パスを使って暗黙のリンク ファイルとして、またはソリューション エクスプローラー内のパスを指定することで明示的なリンク ファイルとして、指定できます。

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

次のいずれかの条件が満たされると、リンク ファイルは無視されます。

- リンク ファイルに Link メタデータが含まれ、Include 属性で指定されたパスがプロジェクト ディレクトリ内に存在する
- リンク ファイルがプロジェクト階層内に存在するファイルと重複する
- リンク ファイルに Link メタデータが含まれ、リンク パスがプロジェクト階層の外部の相対パスである
- リンク パスがルートになっている

### <a name="working-with-linked-files"></a>リンク ファイルの使用

既存の項目をリンクとして追加するには、ファイルを追加するプロジェクトのフォルダーを右クリックし、**[追加] > [既存の項目...]** を選びます。 表示されるダイアログで、ファイルを選び、**[追加]** ボタンのドロップダウンから **[リンクとして追加]** を選びます。 競合するファイルがない場合は、選んだフォルダーにリンクが作成されます。 ただし、同じ名前のファイルが既に存在する場合、またはそのファイルへのリンクがプロジェクト内に既に存在する場合は、リンクは追加されません。

プロジェクト フォルダーに既に存在するファイルにリンクしようとした場合は、リンクとしてではなく通常のファイルとして追加されます。 ファイルをリンクに変換するには、**[ファイル] > [名前を付けて保存]** を選び、プロジェクト階層外の場所にファイルを保存します。Visual Studio は自動的にそれをリンクに変換します。 同様に、**[ファイル] > [名前を付けて保存]** を使ってプロジェクト階層内のどこかにファイルを保存することにより、リンクをファイルに戻すことができます。 

ソリューション エクスプローラーでリンク ファイルを移動すると、リンクは移動されますが、実際のファイルは影響を受けません。 同様に、リンクを削除すると、リンクだけが削除されて、ファイルには影響ありません。

リンク ファイルの名前を変更することはできません。

## <a name="references"></a>参照

Visual Studio のプロジェクトは、プロジェクトと拡張機能への参照の追加をサポートし、参照はソリューション エクスプローラーの **[参照]** ノードに表示されます。

![Python プロジェクトでの拡張機能の参照](media/projects-extension-references.png)

通常、拡張機能の参照は、プロジェクト間の依存関係を示し、設計時に IntelliSense するか、またはコンパイル時にリンクを提供するために使われます。 Python プロジェクトも同様の方法で参照を使いますが、Python の動的な性質のため、主として設計時に強化された IntelliSense を提供するために使われます。 また、追加の依存関係をインストールするために Microsoft Azure への配置で使うこともできます。

### <a name="extension-modules"></a>拡張モジュール

`.pyd` ファイルへの参照により、生成されるモジュールに対する IntelliSense が有効になります。 Visual Studio は `.pyd` ファイルを Python インタープリターに読み込み、その型と関数を調べます。 また、関数でシグネチャ ヘルプを提供するためにドキュメントの文字列の解析を試みます。

ディスクで拡張モジュールが更新された場合、Visual Studio はバックグラウンドでモジュールを再分析します。 これによる実行時動作への影響はありませんが、分析が完了するまで一部の入力候補が使えなくなります。

また、モジュールを含むフォルダーへの[検索パス](python-environments.md#search-paths)の追加が必要になることもあります。

### <a name="net-projects"></a>.NET プロジェクト

IronPython を使う場合は、.NET アセンブリへの参照を追加して IntelliSense を有効にすることができます。 ソリューション内の .NETプロジェクトの場合は、Python プロジェクトで **[参照]** ノードを右クリックし、**[参照の追加]** を選び、**[プロジェクト]** タブを選んで、目的のプロジェクトを参照します。 別にダウンロードした DLL の場合は、代わりに **[参照]** タブを選び、目的の DLL を参照します。

IronPython での参照は、`clr.AddReference('AssemblyName')` への呼び出しが行われるまで使えないので、`clr.AddReference` の呼び出しをアセンブリに追加する必要もあります。

### <a name="webpi-projects"></a>WebPI プロジェクト

配置用の WebPI 製品エントリへの参照を Microsoft Azure クラウド サービスに追加し、クラウドで WebPI フィードを使って追加コンポーネントをインストールできます。 既定では、表示されるフィードは Python 固有であり、Django、CPython、およびその他の主要なコンポーネントが含まれます。 次に示すように、独自のフィードを選ぶこともできます。 Microsoft Azure に発行すると、セットアップ タスクは参照されているすべての製品をインストールします。

![WebPI の参照](media/projects-webPI-components.png)
