---
title: Azure App Service への発行 - Visual Studio for Mac
ms.date: 01/17/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac-dev15
ms.workload:
- azure
ms.openlocfilehash: 41eda3bf79b60e7d0a07b41fdd50bbf588240c3d
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55089485"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Visual Studio for Mac を使用して Azure App Service に Web アプリを発行する

発行ツールを使用して、Azure App Service に ASP.NET Core アプリを発行することができます。

## <a name="prerequisites"></a>必須コンポーネント

 - ASP.NET Core を有効にしてインストールされた [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs4mac2017)。
 - Azure サブスクリプション。 サブスクリプションがまだない場合は、[無料でサインアップ](https://azure.microsoft.com/free/dotnet/)します。これには、30 日間の $200 のクレジットと、12 か月間の人気の無料サービスが含まれます。
 - ASP.NET Core プロジェクト。 プロジェクトをまだ用意していない場合は、[新しいプロジェクトを作成](https://docs.microsoft.com/visualstudio/mac/create-new-projects?view=vsmac-2017)することができます。

## <a name="publish-to-azure-app-service"></a>Azure App Service に発行する

 1. Solution Pad で、プロジェクトを右クリックして、**[発行]** を選択します。

    ![[発行] コンテキスト メニュー](media/publish-context-menu.png)

 2. このプロジェクトを既に Azure App Service に発行している場合は、メニューに発行プロファイルが表示されます。 その発行プロファイルを選択して、発行プロセスを開始します。

 3. このプロジェクトを初めて App Service に発行する場合は、**[Azure に発行する]** を選択します

    ![App Service コンテキスト メニューに発行する](media/publish-to-azure-context-menu.png)

 4. **[Azure App Service に発行する]** ダイアログが表示され、既存の App Services がすべて表示されます。 既存の App Service に発行するには、リストの App Service を選択して **[発行]** をクリックします。

    ![[Azure App Service に発行する] ダイアログ](media/publish-to-app-service-dialog.png)

 5. 新しい App Service を作成するには、**[新規作成]** をクリックします。 

    ![[App Service に発行する] ダイアログ](media/publish-to-app-service-dialog-new-selected.png)

 6. **[新しい App Service]** ダイアログが表示されます。 このダイアログで、新しい App Service 用の設定を構成できます。

    ![[新しい App Service] ダイアログ](media/publish-new-app-service.png)

    ここには、カスタマイズを検討できるいくつかのオプションがあります。 既定では、App Service の名前はプロジェクト名になります。 名前を利用できない場合は、警告マークが入力フィールドの右側に表示されます。 App Service の名前は自分の Web サイトの URL で使用されるため、名前は URL で使用できる必要があります。

    **[サブスクリプション]** ドロップダウンを使用して、App Service が関連付けられるサブスクリプションを変更できます。

    ドロップダウンを使って既存の**リソース グループ**を選択するか、または **+** ボタンで新しいリソース グループを作成できます。

    App Service プランでは、既存のプランを選択するか、**[カスタム]** ラジオ ボタンを選択することで新しいプランを作成します。

    新しい App Service を作成して、自分のプロジェクトをそこに発行するには、**[作成]** をクリックします。

    **[作成]** をクリックしたら、**[新しい App Service]** ダイアログが閉じられ、App Service の作成が開始されたことを示す次のメッセージが表示されます。

      ![App Service のメッセージを作成する](media/publish-create-app-service-message.png)

    **[OK]** をクリックすると、メッセージが閉じられ、自分のプロジェクトの作業を続けることができます。 IDE の上部にあるステータス バーで、発行プロセスの状態を確認することができます。 Web アプリが正常に発行されると、既定のブラウザーでそのサイトが開かれます。