---
title: "Azure App Service での Python の管理 | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 56fccdd5e103cf29c8ea4a93ab80de7187275642
ms.contentlocale: ja-jp
ms.lasthandoff: 08/01/2017

---

# <a name="managing-python-on-azure-app-service"></a>Azure App Service での Python の管理

[Azure App Service](https://azure.microsoft.com/services/app-service/) は、Web アプリに提供するサービスとしてのプラットフォームです。Web アプリがブラウザーでアクセスされるサイト、自身のクライアントで使用される REST API、またはイベント トリガーされる処理かどうかは関係ありません。 App Service は、Python を使用してアプリの実装を完全にサポートします。

Azure App Service での Python のサポートは、App Service サイトの拡張機能のセットとして提供されます。拡張機能にはそれぞれ Python ランタイムの特定のバージョンが含まれています。 当然ながら、推奨されるのは最新の Python 3 バージョンですが、必要に応じて古いバージョンを選択することもできます。 このトピックでは、サイト拡張機能を目的のパッケージと共にインストールして構成する方法について説明します。

> [!Note]
> ここで説明するプロセスは、特に改善のために変更される可能性があります。 変更は、[Python Engineering at Microsoft のブログ](https://blogs.msdn.microsoft.com/pythonengineering/)で発表されます。

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Azure Portal から Python のバージョンを選択する

サイトが既にデプロイ済みで Azure App Service で実行されている場合は、App Service ブレードに移動し、**[開発ツール]** セクションまでスクロールして、**[拡張機能] > [追加]** を選択します。 リストをスクロールして目的の Python のバージョンに特定の拡張機能を見つけます  (残念ながら、リストは並べ替えできないため、異なるバージョンがリスト内に散らばっている場合がよくあります)。

![Python の拡張機能を示す Azure Portal](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Azure Resource Manager から Python のバージョンを選択する

Azure Resource Manager テンプレートを使用してサイトをデプロイしている場合は、サイト拡張機能をリソースとして追加します。 拡張機能は、サイトの入れ子になったリソースとして、型 `siteextensions` と [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22) からの名前で表示されます。

たとえば、`python361x64` (Python 3.6.1 x 64) への参照を追加すると、テンプレートは、次のようになります。

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
      "resources": [
        {
          "apiVersion": "2015-08-01",
          "name": "python361x64",
          "type": "siteextensions",
          "properties": { },
          "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
          ]
        },
      ...
```

## <a name="configuring-your-site"></a>サイトを構成する

(ポータルまたは Azure Resource Manager テンプレートのいずれかを使って) サイト拡張機能をインストールすると、Python のインストール パスは `d:\home\python361x64\python.exe` のようになります。 特定のパスを表示するには、自分の App Service に対して表示されるリストで拡張機能を選択し、パスを含む説明ページを開きます。

![Azure App Service での拡張機能のリスト](media/python-on-azure-extension-list.png)

![Azure App Service での拡張機能の詳細](media/python-on-azure-extension-detail.png)

次の手順は、FastCGI および Http Platform の両方の要求ハンドラーに対するサイトの `web.config` ファイル内の Python インストールを参照することです。

### <a name="using-the-fastcgi-handler"></a>FastCGI ハンドラーを使用する

FastCGI は、要求レベルで動作するインターフェイスです。 IIS は、受信接続を受信し、各要求を 1 つ以上の永続的な Python プロセスで実行されている WSGI アプリへ転送します。 [wfastcgi パッケージ](https://pypi.io/project/wfastcgi)はプレインストールされ、各 Python のサイト拡張機能で構成されているため、次のコードを `web.config` に含めることで簡単に有効にできます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` はアプリで環境変数として使用できます。
- `PYTHONPATH` の値は、自由に拡張できますが、サイトのルートを含める必要があります。
- `WSGI_HANDLER` はサイトからインポート可能な WSGI アプリをポイントする必要があります。
- `WSGI_LOG` は省略可能ですが、サイトのデバッグのために推奨します。 

`<handlers>` の下で、`<add>` 要素内の `scriptProcessor` 属性に特定のインストールへの適切なパスが含まれていることを確認します。 パスは、拡張機能の詳細ブレードでもう一度表示されます。

### <a name="using-the-http-platform-handler"></a>Http Platform ハンドラーを使用する

HttpPlatform モジュールは、スタンドアロンの Python プロセスに直接ソケット接続を渡します。 このパススルーにより、任意の Web サーバーを実行することができますが、ローカル Web サーバーを実行するスタートアップ スクリプトが必要になります。 `<httpPlatform>` 要素でスクリプトを指定します。ここで、`processPath` 属性は Python をポイントし、`arguments` 属性はスクリプトと指定する任意の引数をポイントします。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

構成での `python.exe` へのパスは、当然ながら、インストールした特定のバージョンになります。

コードに示されている `HTTP_PLATFORM_PORT` 環境変数には、ローカル サーバーが localhost からの接続をリッスンするポートが含まれています。 この例では、必要に応じて、別の環境変数 (この場合は `SERVER_PORT`) を作成する方法も示しています。

## <a name="installing-packages"></a>パッケージのインストール

アプリはさまざまなパッケージに依存している可能性があるため、次の 3 つのいずれかの方法で、これらのパッケージが App Service の Python 環境にインストールされていることを確認します。

- Azure Portal の Azure App Service コンソール
- Kudu REST API
- アプリ ソース コードに各ライブラリをコピーする

### <a name="kudu-console"></a>Kudu コンソール

[Kudu コンソール](https://github.com/projectkudu/kudu/wiki/Kudu-console)は、App Service サーバーとそのファイル システムに直接アクセスするための昇格されたコマンド ライン アクセスを提供します。 これは重要なデバッグ ツールであるだけでなく、CLI ベースの構成にも使用できます。

App Service ブレードから Kudu にアクセスするには、**[開発ツール] > [高度なツール]** を選択し、**[移動]** を選択し、App Service のベース URL に `.scm` が挿入された URL に移動します。 たとえば、ベース URL が `https://vspython-test.azurewebsites.net/` の場合、Kudu は `https://vspython-test.scm.azurewebsites.net/` にあります。

![Azure App Service の Kudu コンソール](media/python-on-azure-console01.png)

**[デバッグ コンソール] > [CMD]** を選択してコンソールを開きます。このコンソールで Python のインストール環境に移動し、既存のライブラリを確認できます。

1 つのパッケージをインストールするには、次の手順を実行します。

1. パッケージのインストール先の Python のインストール フォルダーに移動します (`d:\home\python361x64` など)。
1. `python.exe -m pip install <package_name>` を使用してパッケージをインストールします。

![Azure App Service の Kudu コンソールを使用して matplotlib をインストールする例](media/python-on-azure-console02.png)

`requirements.txt` (推奨) からパッケージをインストールするには、次の手順を実行します。

1. パッケージのインストール先の Python のインストール フォルダーに移動します (`d:\home\python361x64` など)。
1. `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` を使用してパッケージをインストールします。

requirements.txt は、ローカルおよびサーバーで設定されたのと同じパッケージを簡単に再現できるため、これを使用することをお勧めします。

> [!Note]
> Web サーバーには C コンパイラがないため、ネイティブ拡張モジュールを使用して任意のパッケージのホイールをインストールする必要があります。 多くの普及しているパッケージでは、独自のホイールを提供しています。 提供していないパッケージの場合は、ローカルの開発用コンピューターで `pip wheel <package_name>` を使用してホイールをサイトにアップロードします。 例については、「[必要なパッケージの管理](python-environments.md#managing-required-packages)」を参照してください。

### <a name="kudu-rest-api"></a>Kudu REST API

Azure Portal から Kudu コンソールを使用する代わりに、`https://yoursite.scm.azurewebsites.net/api/command` にコマンドをポストすることで、Kudu REST API からコマンドをリモートで実行することができます。 たとえば、`matplotlib` パッケージをインストールするには、次の JSON を `/api/command` にポストします。

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

コマンドと認証の詳細については、[Kudu のドキュメント](https://github.com/projectkudu/kudu/wiki/REST-API)を参照してください。 Azure CLI から [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) を使用して資格情報を表示することもできます。 Kudu コマンドをポストするためのヘルパー ライブラリは [GitHub で入手](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42)することもできます。


### <a name="copying-libraries-into-app-source-code"></a>アプリのソース コードにライブラリをコピーする

サーバーに直接パッケージをインストールする代わりに、独自のソース コードにライブラリをコピーし、それをアプリの一部としてデプロイすることができます。 依存関係の数とそれらの更新頻度によっては、これは実用的なデプロイを開始するための最も簡単な方法になる場合があります。

注意事項は、これらのライブラリがサーバー上の Python のバージョンと正確に一致している必要があることです。一致していない場合、デプロイ後に原因不明のエラーが発生します。 しかし、App Service のサイト拡張機能での Python のバージョンは、python.org でリリースされたものとまったく同じであるため、ローカル開発のために互換性のあるバージョンを簡単に取得できます。

### <a name="avoiding-virtual-environments"></a>仮想環境を回避する

仮想環境でローカルに作業することは、サイトで必要な依存関係を完全に理解するのに役立ちますが、App Service で仮想環境を使用することはお勧めできません。 代わりに、ライブラリをメインの Python フォルダーにインストールし、アプリを使ってそれらをデプロイして、依存関係の競合を回避します。

