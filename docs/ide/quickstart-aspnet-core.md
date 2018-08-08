---
title: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する
description: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する方法について段階的に説明します。
ms.custom: mvc
ms.date: 07/20/2018
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
ms.openlocfilehash: cbb43f61aab1df099efca01b56a927cf189a808e
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468979"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>クイック スタート: Visual Studio を使用して初めての ASP.NET Core Web アプリを作成する

Visual Studio の使用方法を紹介する、この 5 - 10 分のクイック スタートでは、ASP.NET プロジェクト テンプレートと C# プログラミング言語を使って、簡単な "Hello World" Web アプリを作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、ASP.NET Core Web アプリケーション プロジェクトを作成します。 このプロジェクト タイプには、Web アプリを作成するためのすべてのテンプレート ファイルが付属しているので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで **[Visual C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[ASP.NET Core Web アプリケーション]** を選択ます。 次に、ファイル名を「`HelloWorld`」にして、**[OK]** を選択します。

   ![C# 用の新しい ASP.NET Core Web アプリケーション プロジェクトを作成する](../ide/media/csharp-aspnet-choose-template-name-file.png)

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

1. **[新しい ASP.NET Core Web アプリケーション]** ダイアログ ボックスで、上部のドロップダウン メニューに **[ASP.NET Core 2.0]** が表示されていることを確認します。 その後、**[Web アプリケーション]** を選択して **[OK]** を選択します。

   ![[新しい ASP.NET Core Web アプリケーション] ダイアログ ボックス](../ide/media/quickstart-aspnet-core20.png)

すぐに、Visual Studio でプロジェクト ファイルが開きます。

## <a name="create-the-app"></a>アプリを作成する

1. **ソリューション エクスプローラー**で、**Pages** フォルダーを展開し、**About.cshtml** を選択します。

   ![ソリューション エクスプローラーから About.cshtml ファイルを選択する](../ide/media/csharp-aspnet-about-page-html-file.png)

   このファイルは、Web アプリの **About** という名前のページに対応します。

   ![Web アプリの About ページ](../ide/media/csharp-aspnet-about-page.png)

   エディターに、**About** ページの "additional information" 領域の HTML コードが表示されます。

   ![Visual Studio エディターに表示された "additional information" 領域の HTML コード](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. "additional information" というテキストを「**Hello World!**」に変更します。

   ![Visual Studio エディターに表示される既定の "additional information" 領域の HTML コードを変更する](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. **ソリューション エクスプローラー**で、**About.cshtml** を展開し、**About.cshtml.cs** を選択します。 (このファイルも、Web アプリの **About** ページに対応しています。)

   ![ソリューション エクスプローラーから About.cshtml ファイルを選択する](../ide/media/csharp-aspnet-about-page-code-file.png)

   エディターに、**About** ページの "application description" 領域のテキストを含む C# コードが表示されます。

   ![Visual Studio エディターに表示されたアプリケーション説明領域の C# コード](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "application description" というメッセージ テキストを「**What's my message?**」に変更します。

   ![Visual Studio エディターでアプリケーション説明領域の既定のメッセージ テキストを変更する](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>アプリを実行する

1. **Ctrl** + **F5** キーを押してアプリを実行し、Web ブラウザーで開きます。

   > [!NOTE]
   > "**Web サーバー 'IIS Express' に接続できませんでした**" というエラー メッセージが表示される場合は、Visual Studio を閉じて、右クリックまたはコンテキスト メニューから **[管理者として実行]** オプションを使用して Visual Studio を開きます。 その後、アプリケーションをもう一度実行します。

1. Web ページの上部で **[About]** を選択します。

   ![Web ページで [About] を選択する](../ide/media/csharp-aspnet-home-page-about.png)

1. **[About]** ページに追加した更新後のテキストが表示されます。

   ![追加したテキストを含む更新後の [About] ページが表示される](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web ブラウザーを閉じます。

このクイック スタートは完了しました。 C#、ASP.NET Core、Visual Studio IDE (統合開発環境) について少しはご理解いただけたかと思います。

## <a name="next-steps"></a>次の手順

詳細については、引き続き以下のチュートリアルをご覧ください。

> [!div class="nextstepaction"]
> [Visual Studio での C# および ASP.NET の概要](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>関連項目

[Visual Studio を使用して Azure App Service に Web アプリを発行する](..//deployment/quickstart-deploy-to-azure.md)
