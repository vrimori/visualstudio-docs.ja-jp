---
title: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する
description: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する方法について段階的に説明します。
ms.custom: mvc
ms.date: 07/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9978a7eb80a833eeb81796694b958a62a35cd347
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469140"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>クイック スタート: Visual Studio を使用して初めての ASP.NET Core Web アプリを作成する

Visual Studio の使用方法を紹介する、この 5 - 10 分のクイック スタートでは、ASP.NET プロジェクト テンプレートと C# プログラミング言語を使って、シンプルな "Hello World" Web アプリを作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、ASP.NET Core Web アプリケーション プロジェクトを作成します。 ここではその方法を説明します。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで **[Visual C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[ASP.NET Core Web アプリケーション]** を選択ます。 次に、ファイル名を「`HelloWorld`」にして、**[OK]** を選択します。

1. **[新しい ASP.NET Core Web アプリケーション]** ダイアログ ボックスで、上部のドロップダウン メニューに **[ASP.NET Core 2.0]** が表示されていることを確認します。 その後、**[Web アプリケーション]** を選択して **[OK]** を選択します。

  ![Visual Studio で C# ASP.NET Core プロジェクトを作成する方法を示すアニメーション .gif ファイルを表示](../ide/media/csharp-aspnet-animated-create-project.gif)

  すぐに、Visual Studio でプロジェクト ファイルが開きます。

   > [!NOTE]
   > **.NET Core** プロジェクト テンプレートのカテゴリが表示されない場合は、左側のウィンドウで **[Visual Studio インストーラーを開く]** リンクを選択します。
   >
   > ![[新しいプロジェクト] ダイアログ ボックスから Visual Studio インストーラーを開く](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio インストーラーが起動します。 **[ASP.NET と Web 開発]** ワークロードを選択してから **[変更]** を選択します。
   >
   > ![VS インストーラーの ASP.NET ワークロード](../ide/media/quickstart-aspnet-workload.png)
   >
   > (新しいワークロードのインストールを続ける前に、Visual Studio を終了することが必要な場合があります。)

## <a name="create-and-run-the-app"></a>アプリの作成と実行

次に、自分の "Hello World" Web アプリを作成して実行します。 ここではその方法を説明します。

1. **ソリューション エクスプローラー**で、**Pages** フォルダーを展開し、**About.cshtml** を選択します。

   このファイルは、Web アプリの **About** という名前のページに対応します。

   ![Web アプリの About ページ](../ide/media/csharp-aspnet-about-page.png)

1. "additional information" というテキストを「**Hello World!**」に変更します。

1. **ソリューション エクスプローラー**で、**About.cshtml** を展開し、**About.cshtml.cs** を選択します。

1. "application description" というメッセージ テキストを「**What's my message?**」に変更します。

1. **IIS Express** を選択するか、**Ctrl**+**F5** キーを押してアプリを実行し、Web ブラウザーで開きます。

  ![Visual Studio で C# ASP.NET Core Web アプリを作成して実行する方法を示すアニメーション .gif ファイルを表示](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > "**Web サーバー 'IIS Express' に接続できませんでした**" というエラー メッセージが表示される場合は、Visual Studio を閉じて、右クリックまたはコンテキスト メニューから **[管理者として実行]** オプションを使用して Visual Studio を開きます。 その後、アプリケーションをもう一度実行します。

1. **About** ページに更新されたテキストが含まれていることを確認します。

1. Web ブラウザーを閉じます。

このクイック スタートは完了しました。 C#、ASP.NET Core、Visual Studio IDE (統合開発環境) について少しはご理解いただけたかと思います。

## <a name="next-steps"></a>次の手順

詳細については、引き続き以下のチュートリアルをご覧ください。

> [!div class="nextstepaction"]
> [Visual Studio での C# および ASP.NET の概要](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>関連項目

[Visual Studio を使用して Azure App Service に Web アプリを発行する](..//deployment/quickstart-deploy-to-azure.md)
