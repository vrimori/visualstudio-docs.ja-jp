---
title: Python プロジェクトの項目テンプレート
description: Visual Studio の [追加] > [新しい項目] ダイアログから利用できる、Python プロジェクトの項目テンプレートの参照一覧。
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9811905e842eeb62399ef3b88558ee0286b05c84
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032678"
---
# <a name="python-item-templates"></a>Python 項目テンプレート

項目テンプレートは、**ソリューション エクスプローラー**のコンテキスト メニューにある **[プロジェクト]** > **[新しい項目の追加]** メニュー コマンドから、または **[追加]** > **[新しい項目]** コマンドから、Python プロジェクト内で利用できます。

![[新しい項目の追加] ダイアログ ボックス](media/project-item-templates.png)

項目に指定した名前を使用して、テンプレートは通常、プロジェクトで現在選択されているフォルダー内に 1 つ以上のファイルとフォルダーを作成します (フォルダーを右クリックしてコンテキスト メニューを開くと、自動的に該当のフォルダーが選択されます)。 項目を追加すると、Visual Studio プロジェクトに組み入れられ、項目が**ソリューション エクスプローラー**に表示されます。

次の表では、Python プロジェクト内の各項目テンプレートの効果を簡単に説明しています。

| テンプレート | テンプレートによって作成されるもの |
| --- | --- |
| 空の Python ファイル | `.py` 拡張子の空のファイル。 |
| Python クラス | 単一の空の Python クラス定義を含む `.py` ファイル。 |
| Python パッケージ | `__init.py__` ファイルを含むフォルダー。 |
| Python 単体テスト | `unittest` フレームワークに基づく単一の単体テストの `.py` ファイル。ファイル内のテストを実行するための `unittest.main()` の呼び出しを含みます。 |
| HTML ページ | `<head>` および `<body>` 要素で構成される単一のページ構造を備えた `.html` ファイル。 |
| JavaScript | 空の `.js` ファイル。 |
| スタイル シート | `body` の空のスタイルを含む `.css` ファイル。 |
| テキスト ファイル | 空の `.txt` ファイル。 |
| Django 1.9 アプリ<br/>Django 1.4 アプリ | アプリ名のフォルダー。Django 1.9 では [「Visual Studio での Django の詳細情報」の手順 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) で説明したように、Django アプリの主要なファイルを格納します。 Django 1.4 では、`migrations` フォルダー、`admin.py` ファイル、および `apps.py` ファイルは含まれません。 |
| IronPython WPF ウィンドウ | 2 つの横並びのファイルで構成される WPF ウィンドウ: 空の `<Grid>` 要素を含み `<Window>` を定義する `.xaml` ファイルと、`wpf` ライブラリを使用して XAML ファイルを読み込む、関連する `.py` ファイル。 通常は、IronPython プロジェクト テンプレートの 1 つを使用して作成されたプロジェクト内で使用されます。 [Python プロジェクト管理に関するページの「プロジェクト テンプレート」](managing-python-projects-in-visual-studio.md#project-templates)のセクションを参照してください。 |
| Web ロール サポート ファイル | プロジェクト ルートにある `bin` フォルダー (プロジェクト内で選択されたフォルダーとは関連しません)。 Azure クラウド サービス Web ロールの既定のデプロイ スクリプトと `web.config` ファイルが格納されています。 また、テンプレートには、詳細を説明する`readme.html` ファイルが含まれています。 |
| worker ロールのサポート ファイル | プロジェクト ルートにある `bin` フォルダー (プロジェクト内で選択されたフォルダーとは関係ありません)。 Azure クラウド サービス Worker ロールの既定のデプロイ スクリプトと `web.config` ファイルが格納されています。 また、テンプレートには、詳細を説明する`readme.html` ファイルが含まれています。 |
| Azure web.config (FastCGI) | 受信接続の処理に [WSGI](https://wsgi.readthedocs.io/en/latest/) オブジェクトを使うアプリ用のエントリを含む `web.config` ファイル。 このファイルは通常、Azure App Service などの IIS を実行している Web サーバーのルートにデプロイされます。 詳細については、「[Azure App Service への発行](publishing-python-web-applications-to-azure-from-visual-studio.md)」を参照してください。 |
| Azure web.config (HttpPlatformHandler) | 受信接続のためのソケット上でリッスンするアプリのエントリを含む `web.config` ファイル。 このファイルは通常、Azure App Service などの IIS を実行している Web サーバーのルートにデプロイされます。 詳細については、「[Azure App Service への発行](publishing-python-web-applications-to-azure-from-visual-studio.md)」を参照してください。 |
| Azure 静的ファイルの web.config | `web.config` ファイル。通常は `static` フォルダー (または、静的な項目を格納する他のフォルダー) に追加されて、そのフォルダーの Python 処理を無効にします。 この構成ファイルは、上記の FastCGI または HttpPlatformHandler 構成ファイルと組み合わせることで、機能します。 詳細については、「[Azure App Service への発行](publishing-python-web-applications-to-azure-from-visual-studio.md)」を参照してください。 |
| Azure リモート デバッグの web.config | `Microsoft.PythonTools.WebRole.dll` と、リモート デバッグを有効にするためにサーバーにデプロイするモジュールを格納した `ptvsd` フォルダーと共に、WebSockets でリモート デバッグを有効にする `web.config.debug` ファイル。 通常は、`web.config` ファイルと同じ場所にこの項目を作成します。 詳細については、「[Azure 上の Python コードのリモート デバッグ](debugging-remote-python-code-on-azure.md)」を参照してください。 以下の注意事項も確認してください。 |

> [!Note]
> デバッグ `web.config` テンプレートをプロジェクトに追加し、Python リモート デバッグを使用する計画がある場合は、"デバッグ" 構成でサイトを発行する必要があります。 この設定は、現在アクティブなソリューション構成とは別であり、常に既定で "リリース" になります。 変更するには、発行ウィザードで **[設定]** タブを開き、**[構成]** コンボ ボックスを使用します  (Azure Web Apps の作成とデプロイに関する詳細については、[Azure ドキュメント](https://azure.microsoft.com/develop/python/) をご覧ください)。
>
> ![発行構成の変更](media/template-web-publish-config.png)

## <a name="see-also"></a>関連項目

- [Python プロジェクト管理 - プロジェクト テンプレート](managing-python-projects-in-visual-studio.md#project-templates)
- [Python Web プロジェクト テンプレート](python-web-application-project-templates.md)
- [Azure App Service への発行](publishing-python-web-applications-to-azure-from-visual-studio.md)