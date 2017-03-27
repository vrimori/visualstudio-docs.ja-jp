---
title: "Python Tools for Visual Studio の Web プロジェクト テンプレート | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401e7725-8be5-4e67-862c-bf0690a529e3
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 2375c0c3b1a692d03d8790e400e3fea606355831
ms.lasthandoff: 03/10/2017

---

# <a name="python-web-project-templates"></a>Python Web プロジェクト テンプレート

Python Tools for Visual Studio (PTVS) には、Bottle、Django、Flask などのフレームワークで Web プロジェクトを開発するためのサポートが含まれています。 これには、さまざまなフレームワークを処理するように構成できるプロジェクト テンプレートとデバッグ ランチャーが含まれます。 ただし、PTVS には、フレームワーク自体は含まれず、プロジェクトを右クリックして **[Python] > [Install/upgrade framework... (フレームワークのインストール/アップグレード...)]** を選択して別途インストールする必要があります。

各テンプレート (**[ファイル] > [新規] > [プロジェクト]** からアクセス) は、ランダムに選ばれたローカル ポートで Web サーバーを起動し、デバッグ時に既定のブラウザーを開き、[Microsoft Azure](http://www.azure.com) に直接発行できるようにします。 Bottle、Flask、Django 用のテンプレートが用意されており、Pyramid など他のフレームワークには汎用の "Web プロジェクト" テンプレートを使用できます。

![新しい Web プロジェクト テンプレート](media/template-web-new-project.png)

Bottle、Flask、Django の各テンプレートには、いくつかのページと静的ファイルがあるスターター サイトが含まれます。 このコードは、サーバーをローカルに実行およびデバッグするため (一部の設定は環境から取得する必要があります)、また Microsoft Azure にデプロイするため ([WSGI アプリ](http://www.python.org/dev/peps/pep-3333/) オブジェクトを提供する必要があります) に十分です。

フレームワーク固有のテンプレートからプロジェクトを作成する場合、pip を使用して必要なパッケージをインストールするためのダイアログが表示されます。 Web プロジェクトの[仮想環境](python-environments.md#virtual-environments)を使用して、Web サイトのパブリッシュ時に正しい依存関係が含まれるようにすることもお勧めします。

![プロジェクト テンプレートに必要なパッケージをインストールするダイアログ](media/template-web-requirements-txt-wizard.png)

Microsoft Azure App Service にデプロイする場合は、Python のバージョンとして[サイト拡張機能](https://aka.ms/PythonOnAppService)を選び、パッケージを手動でインストールする必要があります。 また、Azure App Service は、Visual Studio からデプロイされるときに `requirements.txt` ファイルからパッケージを自動的にインストール**しない**ため、[aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService) の構成の詳細に従ってください。

これに対して、Microsoft Azure クラウド サービスは `requirements.txt` ファイルをサポートします。 詳しくは、[Azure クラウド サービス プロジェクト](template-azure-cloud-service.md)に関する記事をご覧ください。

Python Web プロジェクトの概要については、「[Getting Started with PTVS, Part 6: Web sites](https://youtu.be/FJx5mutt1uk?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)」(PTVS の概要、パート 6: Web サイト) (youtube.com、3m10s) をご覧ください。

> [!ビデオ https://www.youtube.com/embed/FJx5mutt1uk]

## <a name="debugging"></a>デバッグ

Web プロジェクトのデバッグが開始されると、PTVS は Web サーバーをローカルで起動し、そのアドレスとポートを既定のブラウザーで開きます。 追加のオプションを指定するには、プロジェクトを右クリックし、**[プロパティ]** を選択し、**[Web ランチャー]** タブを選択します。

  ![一般的な Web テンプレートの Web ランチャーのプロパティ](media/template-web-launcher-properties.png)

**[デバッグ]** グループで、次の操作を実行します。

- **[検索パス]**、**[スクリプトの引数]**、**[Interpreter Arguments (インタープリター引数)]**、**[Interpreter Path (インタープリター パス)]**: これらは[通常のデバッグ](debugging.md)の場合と同じです
- **[起動 URL]**: ブラウザーで開かれる URL を指定します。 既定値は `localhost` です。
- **[ポート番号]**: URL に何も指定されなかった場合に使用するポート (PTVS によって既定で自動的に選択されます)。 これにより、ローカル デバッグ サーバーがリッスンするポートを構成するためにテンプレートで使用される `SERVER_PORT` 環境変数の既定値を上書きできます。

**[Run Server Command (サーバー コマンドの実行)]** と **[Debug Server Command (サーバー コマンドのデバッグ)]** グループ (後者はイメージに表示されている内容の下にあります) のプロパティによって、Web サーバーの起動方法が決定されます。 多くのフレームワークでは、現在のプロジェクトの外部のスクリプトを使用する必要があるため、スクリプトをここで構成でき、スタートアップ モジュールの名前をパラメーターとして渡すことができます。

- **[コマンド]**: Python スクリプト (`*.py` ファイル)、モジュール名 (`python.exe -m module_name` など)、または&1; 行のコード (`python.exe -c "code"` など) にすることができます。 ドロップダウンの値は、これらの種類のどれが対象であるかを示します。
- **[引数]**: これらは、コマンド ラインでコマンドに続いて渡されます。
- **[環境]**: 環境変数を指定する `NAME=VALUE` ペアの改行区切りリスト。 これらは、ポート番号や検索パスなど、環境を変更できるすべてのプロパティの後に設定されるため、これらの値を上書きできます。

MSBuild 構文を使用して任意のプロジェクト プロパティまたは環境変数を指定できます。例: `$(StartupFile) --port $(SERVER_PORT)`。
`$(StartupFile)` はスタートアップ ファイルの相対パスで、`{StartupModule}` はスタートアップ ファイルのインポート可能な名前です。 `$(SERVER_HOST)` と `$(SERVER_PORT)` は、**[起動 URL]** プロパティと **[ポート番号]** プロパティによって自動的に設定されるか、**[環境]** プロパティによって設定される通常の環境変数です。

> [!Note]
> **[Run Server Command (サーバー コマンドの実行)]** の値は、**[デバッグ] > [サーバーを起動します]** コマンドまたは Ctrl+F5 で使用されます。**[Debug Server Command (サーバー コマンドのデバッグ)]** グループは、**[デバッグ] > [Start Debug Server (デバッグ サーバーの起動)]** コマンドまたは F5 キーをで使用されます。


### <a name="sample-bottle-configuration"></a>サンプルの Bottle 構成

Bottle Web プロジェクト テンプレートには、必要な構成を実行する定型コードが含まれています。 ただし、インポートされた bottle アプリにはこのコードが含まれていない場合があります、その場合、次の設定はインストールされた `bottle` モジュールを使用してアプリを起動します。

- **[Run Server Command (サーバー コマンドの実行)]** グループ:
    - **[コマンド]**: `bottle` (モジュール)
    - **[引数]**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **[Debug Server Command (サーバー コマンドのデバッグ)]** グループ:
    - **[コマンド]**: `bottle` (モジュール)
    - **[引数]** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

デバッグに PTVS を使用する場合、`--reload` オプションはお勧めしません。

### <a name="sample-pyramid-configuration"></a>サンプルの Pyramid 構成

Pyramid アプリは、現在、`pcreate` コマンドライン ツールを使用して作成するのが最適です。 アプリが作成されたら、[From Existing Python Code (既存の Python コードから)](python-projects.md#creating-a-project-from-existing-files) テンプレートを使用してインポートできます。 その後、**[Generic Web Project (汎用 Web プロジェクト)]** カスタマイズを選択してオプションを構成します。 これらの設定は、Pyramid が `..\env` にある仮想環境にインストールされていることを想定しています。

- **[デバッグ]** グループ:
    - **[サーバー ポート]**: 6543 (または .ini ファイルで構成されているポート)

- **[Run Server Command (サーバー コマンドの実行)]** グループ:
    - [コマンド]: `..\env\scripts\pserve-script.py` (スクリプト)
    - [引数]: `Production.ini`

- **[Debug Server Command (サーバー コマンドのデバッグ)]** グループ:
    - [コマンド]: `..\env\scripts\pserve-script.py` (スクリプト)
    - [引数]: `Development.ini`

> [!Tip]
> Pyramid アプリは通常はソース ツリーの最上部より&1; ディレクトリ レベル深いため、プロジェクトの **[作業ディレクトリ]** プロパティを構成することが必要な場合があります。


### <a name="other-configurations"></a>その他の構成

別のフレームワークの設定を共有する場合、または別のフレームワークの設定を要求する場合は、[GitHub で懸案事項](https://github.com/Microsoft/PTVS/issues)を開きます。

## <a name="publishing-to-azure-app-service"></a>Azure App Service への発行

Azure App Service に発行する主な方法は&2; つあります。 まず、ソース管理からのデプロイは、[Azure ドキュメント](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/)で説明しているように、他の言語と同じ方法で使用できます。 Visual Studio から直接発行するには、プロジェクトを右クリックして **[発行]** を選択します。

![プロジェクトのコンテキスト メニューの [発行] コマンド](media/template-web-publish-command.png)

コマンドを選択した後、ウィザードの指示に従って Web サイトを作成するか発行の設定をインポートし、変更したファイルのプレビューを表示して、リモート サーバーに発行します。

App Service にサイトを作成する場合は、Python と、サイトが依存するパッケージをインストールする必要があります。 最初にサイトを発行することもできますが、Python を構成するまでは実行されません。

App Service に Python をインストールするには、[サイト拡張機能](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net) の使用をお勧めします。 これらは、Python の[公式リリース](https://www.python.org)のコピーで、Azure App Service 用に最適化されて再パッケージ化されています。

サイト拡張機能は、[Azure Portal](https://portal.azure.com/) で App Service の **[開発ツール] > [拡張機能]** ブレードを使用し、**[追加]** を選択し、一覧をスクロールして Python 用の拡張機能を見つけることでデプロイできます。

![Azure Portal へのサイト拡張機能の追加](media/template-web-site-extensions.png)

JSON デプロイ テンプレートを使用している場合は、サイトのリソースとしてサイト拡張機能を指定できます。

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

最後に、[開発コンソール](https://github.com/projectkudu/kudu/wiki/Kudu-console)にログインし、そこからサイト拡張機能をインストールできます。

現時点では、パッケージをインストールするお勧めの方法は、サイト拡張機能をインストールして pip を直接実行した後に開発コンソールを使用することです。 Python の完全なパスを使用することが重要で、そうしないと間違ったものが実行されることがあります。一般に、仮想環境を使用する必要はありません。 例:

```
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Azure App Service にデプロイされた場合、サイトは Microsoft IIS の背後で実行されます。 サイトを IIS と連携できるようにするには、少なくとも `web.config` ファイルを追加する必要があります。 いくつかの一般的なデプロイ ターゲットに対して利用可能なテンプレートがあります。これは、プロジェクトを右クリックし、[**追加] > [新しい項目...] を選択することで使用可能で(下のダイアログを参照)、これらは他で使用するために簡単に変更できます。 使用可能な構成設定について詳しくは、「[IIS Configuration Reference](https://www.iis.net/configreference)」(IIS 構成リファレンス) をご覧ください。

![Azure 項目テンプレート](media/template-web-azure-items.png)

使用可能な項目を以下に示します。

- [Azure web.config (FastCGI)]: アプリが着信接続を処理する [WSGI](https://wsgi.readthedocs.io/en/latest/) オブジェクトを提供する場合の `web.config` ファイルを追加します。
- [Azure web.config (HttpPlatformHandler)]: アプリが着信接続をソケットでリッスンする場合の `web.config` ファイルを追加します。
- [Azure Static files web.config (Azure 静的ファイル web.config)]: 上記のいずれかの `web.config` ファイルがある場合は、これをサブディレクトリに追加して、アプリで処理されないようにします。
- [Azure Remote debugging web.config (Azure リモート デバッグ web.config)]: WebSocket 経由でのリモート デバッグに必要なファイルを追加します。
- [Web Role Support Files (Web ロールのサポート ファイル)]: クラウド サービス Web ロールの既定のデプロイ スクリプトが含まれます。
- [Worker Role Support Files (worker ロールのサポート ファイル)]: クラウド サービス worker ロールの既定のデプロイ スクリプトと起動スクリプトが含まれます。

デバッグ `web.config` テンプレートをプロジェクトに追加し、Python リモート デバッグを使用する計画がある場合は、"デバッグ" 構成でサイトを発行する必要があります。 この設定は、現在アクティブなソリューション構成とは別であり、常に既定で "リリース" になります。 これを変更するには、**[設定]** タブを開き、発行ウィザードの **[構成]** コンボ ボックスを使用します (作成と Azure Web Apps へのデプロイについて詳しくは、[Azure ドキュメント](https://azure.microsoft.com/develop/python/)をご覧ください)。

![発行構成の変更](media/template-web-publish-config.png)

**[Microsoft Azure クラウド サービス プロジェクトに変換]** コマンド (下図) は、クラウド サービス プロジェクトをソリューションに追加します。 このプロジェクトには、使用する仮想マシンとサービスのデプロイ設定と構成が含まれています。 クラウド プロジェクトで **[発行]** コマンドを使用して、クラウド サービスにデプロイする必要があります。Python プロジェクトの **[発行]** コマンドでは、引き続き Web サイトにデプロイされます。 詳しくは、[Azure クラウド サービス プロジェクト](template-azure-cloud-service.md)に関する記事をご覧ください。

![[Microsoft Azure クラウド サービス プロジェクトに変換]コマンド](media/template-web-convert-menu.png)

