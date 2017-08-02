---
title: "Visual Studio から Azure App Service への Python アプリの発行 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 0163d1279b41ef8fecf9ca774cd3e67f0f47f1b1
ms.lasthandoff: 03/07/2017

---

# <a name="publishing-to-azure-app-service"></a>Azure App Service への発行

次の手順に従って、Visual Studio で Python Web サイトの構築をすばやく開始し、Azure App Service に発行することができます。

- [Azure サブスクリプションを作成する](#create-an-azure-subscription)
- [初期プロジェクトを作成してテストする](#create-and-test-the-initial-project)
- [Azure App Service に発行する](#publish-to-azure-app-service)

このプロセスの短いチュートリアルについては、「[Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)」(Visual Studio Python チュートリアル: Web サイトの構築) (youtube.com、3 分 10 秒) をご覧ください。 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>Azure サブスクリプションを作成する

Azure への発行には、Azure サブスクリプションが必要です。または、一時的なサイトを使うこともできます。

サブスクリプションには、[無料の完全な Azure アカウント](https://azure.microsoft.com/en-us/free/)から始めます。これには、Azure サービスのクレジットが含まれます。 [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/) へのサインアップも検討してください。1 年間、毎月&25; ドルのクレジットが提供されます。

Azure サブスクリプションなしで Azure App Service に一時的なサイトを作成するには:

1. ブラウザーを開き、[try.azurewebsites.net](https://try.azurewebsites.net) にアクセスします。
1. アプリの種類で **[Web App]** を選び、**[次へ]** を選びます。
1. テンプレートとして **[空のサイト]** を選び、**[作成 >]** を選びます。
1. 任意のソーシャル ログインを使ってサインインし、しばらくすると、表示される URL でサイトの準備ができます。
1. **[発行プロファイルのダウンロード]** を選び、`.publishsettings` ファイルを保存します。後でこのファイルを使います。

## <a name="create-and-test-the-initial-project"></a>初期プロジェクトを作成してテストする

1. Visual Studio で、**[ファイル] > [新規] > [プロジェクト]** の順に選び、"Bottle" を検索して、**[Bottle Web Project (Bottle Web プロジェクト)]** を選び、**[OK]** をクリックします。    

1. 外部パッケージのインストールを求めるメッセージが表示されたら、**[Install into a virtual environment (仮想環境にインストールする)]** を選びます。 ダイアログの下部にある **[Show required packages (必要なパッケージを表示する)]** コントロールに注意してください。これを使うと、インストールされるパッケージが表示されます。

  ![必要なパッケージのインストール](~/docs/python/media/tutorials-common-external-packages.png)

1. 仮想環境の優先ベース インタープリターを選び (たとえば、**Python 2.7** や **Python 3.4**)、**[作成]** をクリックします。

  ![プロジェクトを作成するときの仮想環境の追加](~/docs/python/media/tutorials-common-add-virtual-environment.png)

1. プロジェクトが作成されたら、**[デバッグ] > [デバッグ開始]** を選ぶか、F5 キーを押して、ローカルにテストします。 既定では、アプリケーションはメモリ内リポジトリを使うので、構成は必要ありません。 Web サーバーが停止すると、すべてのデータが失われます。

1. アプリケーション内をあちこちクリックして、動作を確認します。

1. 終了したら、デバッガーを停止します (**[デバッグ] > [デバッグの停止]** または Shift + F5 キー)。

## <a name="publish-to-azure-app-service"></a>Azure App Service に発行する

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックして、**[発行]** を選びます。 

1. **[発行]** ダイアログで、**[Microsoft Azure App Service]** を選びます。

  ![Azure 発行手順 1](~/docs/python/media/tutorials-common-publish-1.png)

1. ターゲットを選びます。

    - Azure サブスクリプションがある場合は、発行先として **[Microsoft Azure App Service]** を選び、次のダイアログで、既存の App Service を選ぶか、**[新規]** を選んで新しく作成します。
    - try.azurewebsites.net から一時的なサイトを使っている場合は、発行先として **[インポート]** を選び、サイトからダウンロードした `.publishsettings` ファイルを参照して、**[OK]** を選びます。

1. App Service の詳細が、**[発行]** ダイアログの **[接続]** タブに表示されます (下図参照)。

  ![Azure 発行手順 2](~/docs/python/media/tutorials-common-publish-2.png)

1. 必要に応じて、**[次へ >]** を選んで追加設定を確認します。 [Azure で Python コードをリモート デバッグする](debugging-azure-remote.md)場合は、**[構成]** を **[デバッグ]** に設定する必要があります。
1. **[発行]** を選びます。 アプリケーションが Azure に配置されると、そのサイトで既定のブラウザーが開きます。 
