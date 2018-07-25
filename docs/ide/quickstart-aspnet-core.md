---
title: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する
description: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する方法について段階的に説明します。
ms.custom: mvc
ms.date: 06/27/2018
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
ms.openlocfilehash: 9d8aa6a6147ff57ba72f1cc69240ef5a7137cd73
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089300"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>クイック スタート: Visual Studio を使用して初めての ASP.NET Core Web アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、単純な C# ASP.NET Core Web アプリケーションを作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、ASP.NET Core Web アプリケーション プロジェクトを作成します。 プロジェクトの種類は、機能的な Web アプリケーションを構成するテンプレート ファイルにあらかじめ用意されています。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスで、左ウィンドウの **[Visual C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[ASP.NET Core Web アプリケーション]** を選択してから **[OK]** を選択します。

     **.NET Core** プロジェクト テンプレートのカテゴリが表示されない場合は、左側のウィンドウで **[Visual Studio インストーラーを開く]** リンクを選択します。 Visual Studio インストーラーが起動します。 **[ASP.NET と Web 開発]** ワークロードを選択してから **[変更]** を選択します。

     ![VS インストーラーの ASP.NET ワークロード](../ide/media/quickstart-aspnet-workload.png)

1. **[新しい ASP.NET Core Web アプリケーション]** ダイアログ ボックスで、上部のドロップダウン メニューから **[ASP.NET Core 2.0]** を選択します  (リストに **ASP.NET Core 2.0** が表示されない場合は、ダイアログ ボックスの上部付近にある黄色のバーに表示される **[ダウンロード]** リンクに従ってインストールしてください)。**[OK]** をクリックします。

   ![[新しい ASP.NET Core Web アプリケーション] ダイアログ ボックス](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>IDE を探索する

1. **ソリューション エクスプローラー**のツールバーで、**Pages** フォルダーを展開し、**[About.cshtml]** を選択してエディターで開きます。 このファイルは、Web アプリケーションの **About** というページに対応します。

1. エディターで、`AboutModel` を選択してから **F12** キーを押すか、コンテキスト (右クリック) メニューから **[定義に移動]** を選択します。 このコマンドで `AboutModel` C# クラスの定義が示されます。

   ![[定義に移動] コンテキスト メニュー](../ide/media/quickstart-aspnet-gotodefinition.png)

1. 次に、シンプルなショートカットを使用して、ファイルの上部にある `using` ディレクティブをクリーンアップします。 灰色表示の using ディレクティブのいずれかを選択すると、キャレットのすぐ下、または左余白に[クイック アクション](../ide/quick-actions.md) (電球) が表示されます。 電球を選択してから、**[不要な using の削除]** を選択します。

     不要な using がファイルから削除されます。

1. `OnGet()` メソッドで、本体を次のコードに変更します。

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. **Environment** と **String** の下には二重の波下線が表示されます。これらの型は範囲外であるためです。 **[エラー一覧]** ツール バーを開くと、そこに同じエラーが一覧表示されます  (**[エラー一覧]** ツール バーが表示されない場合は、上部のメニュー バーで **[表示]** > **[エラー一覧]** の順に選択します)。

   ![エラー一覧](../ide/media/quickstart-aspnet-errorlist.png)

1. エディター ウィンドウで、エラーを含むいずれかの行にカーソルを置き、左余白のクイック アクション (電球) を選択します。 ドロップダウン メニューから、**[using System;]** を選択してファイルの先頭にこのディレクティブを追加し、エラーを解決します。

## <a name="run-the-application"></a>アプリケーションの実行

1. **Ctrl** + **F5** キーを押してアプリケーションを実行し、Web ブラウザーで開きます。

1. Web サイトの上部にある **[バージョン情報]** を選択すると、**About** ページの `OnGet()` メソッドに追加したディレクトリ メッセージが表示されます。

1. Web ブラウザーを閉じます。

> [!NOTE]
> **"Web サーバー 'IIS Express' に接続できませんでした"** というエラー メッセージが表示された場合は、Visual Studio を閉じて、右クリックするかコンテキスト メニューから **[管理者として実行]** オプションを使用して Visual Studio を開きます。 その後、アプリケーションをもう一度実行します。

このクイック スタートは完了しました。 Visual Studio IDE について少しはご理解いただけたかと思います。 機能についてさらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="next-steps"></a>次の手順

このクイック スタートは完了しました。 C#、ASP.NET Core、Visual Studio IDE について少しはご理解いただけたかと思います。 パブリック サーバー上で実行されているアプリを表示するには、次のボタンを選択します。

> [!div class="nextstepaction"]
> [Azure App Service へのアプリの展開](..//deployment/quickstart-deploy-to-azure.md)

さらに学習するには、チュートリアルを続けて、「[Visual Studio での C# および ASP.NET の概要](tutorial-csharp-aspnet-core.md)」と「[ASP.NET Core MVC と Visual Studio の概要](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)」に進みます。
