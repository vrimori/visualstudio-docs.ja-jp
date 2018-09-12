---
ms.topic: include
ms.openlocfilehash: ff6523d33e29f4fcc6fd02c08e0a35ac00892829
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "39638391"
---
### <a name="create-a-project-using-django-20"></a>Django 2.0 を使用してプロジェクトを作成する

現時点では、**空の Django Web プロジェクト テンプレート**は、最新の Django 1.x バージョンを使用します。 Django 2.x を使用する最も簡単な方法は、Django 2.x ファイルを Django 1.x プロジェクトにインポートすることです。 このプロセスに沿うことで、Visual Studio プロジェクト テンプレートで扱っている他の詳細機能を利用できます。

1. 前にセクションで説明したように、**空の Django Web プロジェクト** テンプレートを使用して Django 1.x プロジェクトを作成します。 ただし、**This project requires external dependencies**\(このプロジェクトには外部の依存関係が必要です\) というプロンプトで、**[I will install them myself]\(自分でインストールします\)** を選択してください。 このオプションを選択すると、以降の手順でアンインストールする依存関係がインストールされません。

1. コマンド プロンプトを開いて、一時フォルダーに移動します。

1. `pip install django` を実行して、グローバルな Python 環境にある最新の Django パッケージをインストールします。

1. `django-admin startproject <project_name>` を実行します。`<project_name>` は、"HelloDjango" など手順 1 で使用したものと同じプロジェクト名に置き換えてください。 `startproject` コマンドは、*\_\_init\_\_.py*、*settings.py*、*urls.py*、*wsgi.py* のファイルが含まれる `<project_name>` と一致しているフォルダーと一緒に *manage.py* ファイルを作成します。

1. Visual Studio で、次のようにプロジェクト内の Django 1.x ファイルを Django 2.x ファイルに置き換えます。

    1. **ソリューション エクスプローラー**で、**manage.py** および Django アプリ フォルダーを削除します。
    1. プロジェクトを右クリックし、**[追加]** > **[既存の項目]** コマンドを選択し、手順 4 で作成した **manage.py** ファイルに移動して選択し、**[OK]** をクリックします。 Visual Studio で、このファイルがプロジェクトにコピーされます。
    1. もう一度プロジェクトを右クリックし、**[追加]** > **[既存の項目]** コマンドを選択し、手順 4 で作成したアプリ フォルダーに移動して選択し、**[OK]** をクリックします。 Visual Studio で、このフォルダー全体とその中の 4 つのファイルがプロジェクトにコピーされます。
    1. **manage.py** を右クリックして、**[Set as Startup File]\(スタートアップ ファイルとして設定\)** を選択します。

    > [!Important]
    > Visual Studio プロジェクトに示されたアプリ名は、`django-admin` ユーティリティで使用された `<project_name>` と一致している必要があります。これは、ユーティリティでは、Python コード ファイル内でその名前を名前空間として使用するためです。

1. *requirements.txt* を開き、その内容を `django >=2.0, <3` に変更して、ファイルを保存します。

1. **ソリューション エクスプローラー**で **[Python 環境]** ノードを右クリックし、**[仮想環境を追加]** を選択します。 表示されたダイアログボックスで、既定値を受け入れて、**[作成]** を選択します。 管理者特権のプロンプトをすべて承諾します。