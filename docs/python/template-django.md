---
title: "Visual Studio での Python 用 Django Web プロジェクト テンプレート | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 4a5db2deb3633e8305dbf83cbe6ba8c0e3344c72
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---

# <a name="django-web-project-template"></a>Django Web プロジェクト テンプレート

[Django](https://www.djangoproject.com/) は、高速、安全、スケーラブルな Web 開発用に設計されたハイレベルの Python フレームワークです。 Visual Studio の Python サポートには、Django ベースの Web アプリケーションの構造を設定するためのプロジェクト テンプレートが用意されています。 Visual Studio でテンプレートを使用するには、**[ファイル] > [新規] >[プロジェクト]** を選択し、「Django」を検索して、"Django Web プロジェクト" テンプレートを選びます。 作成されるプロジェクトには、定型コードと既定の SQLite データベースが含まれます。 "空の Django Web プロジェクト" テンプレートも似ていますが、これにはデータベースが含まれません。

Visual Studio は、Django プロジェクトの完全な IntelliSense を提供します。

- テンプレートに渡されるコンテキスト変数:

    ![コンテキスト変数用の IntelliSense](~/python/media/template-django-intellisense.png)

- 組み込みとユーザー定義両方のタグ付けとフィルター処理:

    ![タグとフィルターの IntelliSense](~/python/media/template-django-intellisense-filter.png)

- 埋め込みの CSS と JavaScript の構文の色分け表示:

    ![CSS Intellisense](~/python/media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](~/python/media/template-django-intellisense-js.png)


また、Visual Studio は Django プロジェクトの完全な[デバッグ サポート](debugging.md)も提供します。 

![ブレークポイント](~/python/media/template-django-debugging.png)

## <a name="django-management-console"></a>Django 管理コンソール

Django 管理コンソールには、**[プロジェクト]** メニューのさまざまなコマンドを使用するか、ソリューション エクスプローラーでプロジェクトを右クリックしてアクセスします。

- **[Open Django Shell... (Django シェルを開く...)]**: モデルを操作できるアプリケーション コンテキストでシェルを起動します

    ![コンソール](~/python/media/template-django-console-shell.png)

- **[Django Sync DB (Django 同期 DB)]**: `manage.py syncdb` を対話型ウィンドウで実行します。

    ![コンソール](~/python/media/template-django-console-sync-db.png)

- **[Collect Static (静的収集)]**: `manage.py collectstatic --noinput` を実行して、`settings.py` の `STATIC_ROOT` で指定されたパスにすべての統計ファイルをコピーします。 [Microsoft Azure に発行](template-web.md#publishing-to-azure-app-service)する場合、統計ファイルは発行操作の一部として収集されます。

    ![コンソール](~/python/media/template-django-console-collect-static.png)

- **[検証]**: `settings.py` の `INSTALLED_APPS` で指定されたインストール済みのモデルで検証エラーをレポートする `manage.py validate` を実行します。

    ![コンソール](~/python/media/template-django-console-validate.png)
