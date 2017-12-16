---
title: "Visual Studio のローカル フォルダーに配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8696e7ffb4120bae12538a03b77d62c0d091a7
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Web アプリまたは .NET Core アプリを Visual Studio 発行ツールを使用してローカル フォルダーに配置します。

使用することができます、**発行**をローカル フォルダーにアプリを公開するツールです。 

次の手順は、ASP.NET、ASP.NET Core、.NET Core および Visual Studio での Python アプリに適用されます。 For Node.js、手順がサポートされますが、ユーザー インターフェイスが異なる。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、次のように選択します。**ファイル > 新しいプロジェクト**です。

1. **Visual c#**または**Visual Basic**、選択**.NET Core**、中央のペインの **コンソール アプリケーション (.NET Core)**です。

1. ような名前を入力**MyLocalApp**  をクリック**OK**です。

    Visual Studio では、プロジェクトを作成します。

## <a name="deploy-to-a-local-folder"></a>ローカル フォルダーに配置します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックして選択**発行**です。

    ![選択発行](../deployment/media/quickstart-publish.png "選択発行")

1. **発行** ウィンドウで、選択**フォルダー**です。

    ![フォルダーを選択](../deployment/media/quickstart-publish-folder.png "フォルダーを選択します")

1. パスを入力またはクリックして**参照**ローカル フォルダーを参照します。

1. **[発行]**をクリックします。

    Visual Studio は、プロジェクトをビルドし、指定されたフォルダーに発行します。

    発行ペインは、概要、プロファイルを示しています。

1. 展開設定を構成する をクリックして**設定**プロファイルの概要にします。

    ![プロファイルの設定](../deployment/media/quickstart-profile-settings.png "プロファイルの設定") 

1. デバッグまたはリリース構成を展開し、をクリックするかどうかなどのオプションを構成する**保存**です。

1. クリックして、再パブリッシュする**発行**です。

発行したファイルは、任意の方法で展開できます。 たとえば、Zip ファイル内にパッケージ化、単純なコピー コマンドを使用して、または任意のインストール パッケージに配置できます。

## <a name="next-steps"></a>次のステップ

- [発行ツールを使用して .NET Core アプリケーションの配置します。](https://docs.microsoft.com/en-us/dotnet/core/deploying/deploy-with-vs)
- [Microsoft ストア (デスクトップ ブリッジ) のデスクトップ アプリをパッケージ化します。](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET)[.NET Framework およびアプリケーションの展開](https://docs.microsoft.com/en-us/dotnet/framework/deployment/)
