---
title: Visual Studio のローカル フォルダーに配置 |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/08/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016538bded47a5186294c161cc7f310b26818d15
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764220"
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Web アプリまたは .NET Core アプリを Visual Studio 発行ツールを使用してローカル フォルダーに配置します。

ローカル フォルダーにアプリを公開するために **発行**ツール を使用することができます。

次の手順は、ASP.NET、ASP.NET Core、.NET Core および Visual Studio での Python アプリに適用されます。 For Node.js、手順がサポートされますが、ユーザー インターフェイスが異なる。

## <a name="prerequisites"></a>必須コンポーネント

* インストールされている Visual Studio 2017 が必要とします。**NET デスクトップ開発**ワークロードと **。NET コア**ワークロード。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#** または**Visual Basic**、選択 **.NET Core**、し、中央のペインで次のように選択します。**コンソール アプリケーション (.NET Core)** です。

1. ような名前を入力**MyLocalApp**  をクリック**OK**です。

    Visual Studio によってプロジェクトが作成されます。

## <a name="deploy-to-a-local-folder"></a>ローカル フォルダーに配置する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

    ![選択発行](../deployment/media/quickstart-publish.png "選択発行")

1. 任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイルを作成**です。

1. **発行先の選択** ダイアログ ボックスで、選択**フォルダー**です。

    ![フォルダーを選択](../deployment/media/quickstart-publish-folder.png "フォルダーを選択します")

1. パスを入力またはクリックして**参照**ローカル フォルダーを参照します。

1. **[発行]** をクリックします。

    Visual Studio は、プロジェクトをビルドし、指定されたフォルダーに発行します。

    発行ペインは、概要、プロファイルを示しています。

1. 展開設定を構成する をクリックして**設定**プロファイルの概要にします。

    ![プロファイルの設定](../deployment/media/quickstart-profile-settings.png "プロファイルの設定") 

1. デバッグまたはリリース構成を展開し、をクリックするかどうかなどのオプションを構成する**保存**です。

1. クリックして、再パブリッシュする**発行**です。

発行したファイルは、任意の方法で展開できます。 たとえば、Zip ファイル内にパッケージ化、単純なコピー コマンドを使用して、または任意のインストール パッケージに配置できます。

## <a name="next-steps"></a>次の手順

- [発行ツールを使用して .NET Core アプリケーションを配置する](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Microsoft ストアのデスクトップ アプリをパッケージ化する (デスクトップ ブリッジ)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET)[.NET Framework とアプリケーションを展開しています.](/dotnet/framework/deployment/)
