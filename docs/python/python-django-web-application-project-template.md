---
title: Python 用 Django Web プロジェクト テンプレート
description: Django フレームワークを使って Python で書かれた Web アプリケーション用の Visual Studio テンプレートの概要です。
ms.date: 07/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e847322b1bbbefec5c7013d7e90475e08f42694b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499544"
---
# <a name="django-web-project-template"></a>Django Web プロジェクト テンプレート

[Django](https://www.djangoproject.com/) は、高速、安全、スケーラブルな Web 開発用に設計されたハイレベルの Python フレームワークです。 Visual Studio の Python サポートには、Django ベースの Web アプリケーションの構造を設定するためのプロジェクト テンプレートがいくつか用意されています。 Visual Studio でテンプレートを使用するには、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し、"Django" を探し、**[空の Django Web プロジェクト]**、**[Django Web プロジェクト]**、および **[ポーリング Django Web プロジェクト]** テンプレートから選択します。 すべてのテンプレートのチュートリアルについては、[Django チュートリアルの概要](learn-django-in-visual-studio-step-01-project-and-solution.md)に関するページを参照してください。

Visual Studio は、Django プロジェクトの完全な IntelliSense を提供します。

- テンプレートに渡されるコンテキスト変数:

    ![コンテキスト変数用の IntelliSense](media/template-django-intellisense.png)

- 組み込みとユーザー定義両方のタグ付けとフィルター処理:

    ![タグとフィルターの IntelliSense](media/template-django-intellisense-filter.png)

- 埋め込みの CSS と JavaScript の構文の色分け表示:

    ![CSS Intellisense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

また、Visual Studio は Django プロジェクトの完全な[デバッグ サポート](debugging-python-in-visual-studio.md)も提供します。 

![ブレークポイント](media/template-django-debugging.png)

Django プロジェクトは *manage.py* ファイルで管理するのが一般的であり、Visual Studio でもそのようになっています。 エントリ ポイントとしてそのファイルの使用を止めると、基本的にプロジェクト ファイルは壊れます。 その場合は、Django プロジェクトにしないで、[既存のファイルからプロジェクトを作成しなおす](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files)必要があります。

## <a name="django-management-console"></a>Django 管理コンソール

Django 管理コンソールには、**[プロジェクト]** メニューのさまざまなコマンドを使用するか、**ソリューション エクスプローラー**でプロジェクトを右クリックしてアクセスします。

- **[Django シェルを開く]**: モデルを操作できるアプリケーション コンテキストでシェルを起動します。

    ![コンソール](media/template-django-console-shell.png)

- **[Django Sync DB]**: `manage.py syncdb` を**対話型**ウィンドウで実行します。

    ![コンソール](media/template-django-console-sync-db.png)

- **[静的ファイルの収集]**: `manage.py collectstatic --noinput` を実行して、*settings.py* の `STATIC_ROOT` で指定されたパスにすべての統計ファイルをコピーします。 [[Microsoft Azure に発行]](publishing-python-web-applications-to-azure-from-visual-studio.md) を選択すると、統計ファイルは発行操作の一部として収集されます。

    ![コンソール](media/template-django-console-collect-static.png)

- **[検証]**: *settings.py* の `INSTALLED_APPS` で指定されたインストール済みのモデルで検証エラーをレポートする `manage.py validate` を実行します。

    ![コンソール](media/template-django-console-validate.png)

## <a name="see-also"></a>関連項目

- [Django チュートリアルの概要](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Azure App Service に発行する](publishing-python-web-applications-to-azure-from-visual-studio.md)