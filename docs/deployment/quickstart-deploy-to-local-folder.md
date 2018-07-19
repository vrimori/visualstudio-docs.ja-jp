---
title: ローカル フォルダーに配置する
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781914"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Visual Studio を使用したローカル フォルダーにアプリをデプロイします。

使用することができます、**発行**Visual Studio からローカル フォルダーに ASP.NET、ASP.NET Core、.NET Core、および Python のアプリを発行するためのツール。 For Node.js が手順がサポートされていますが、ユーザー インターフェイスは異なります。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>ローカル フォルダーに配置する

1. ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**発行**(を使用して、または、**ビルド** > **発行**メニュー項目)。

    ![ソリューション エクスプ ローラーでプロジェクトのコンテキスト メニューの [発行] コマンド](../deployment/media/quickstart-publish.png "発行の選択")

1. 以前に任意の発行プロファイルを構成する場合、**発行**ウィンドウが表示されます。 選択**新しいプロファイルを作成する**します。

1. **発行先を選択** ダイアログ ボックスで、選択**フォルダー**します。

    ![公開ターゲットとしてローカル フォルダーを選択](../deployment/media/quickstart-publish-folder.png "フォルダーの選択")

1. パスを入力または選択**参照**ローカル フォルダーを指定します。

1. **[発行]** を選びます。 Visual Studio は、プロジェクトをビルドし、指定したフォルダーに発行します。 プロジェクトのプロパティ**発行**概要プロファイルを示すウィンドウが表示されます。

    ![発行プロファイルの概要を示すプロパティ ウィンドウ](../deployment/media/quickstart-publish-folder-summary.png)

1. 展開の設定を構成するには、選択**構成**概要や選択プロファイルで、**設定**タブ。

    ![プロファイルの設定](../deployment/media/quickstart-profile-settings.png "プロファイルの設定")

1. など、デバッグまたはリリース構成をデプロイしを選択するかどうかのオプションを構成する**保存**します。

1. 再発行するには、次のように選択します。**発行**します。

発行したファイルは、任意の方法で展開できます。 パッケージなど、 *.zip*ファイル、単純なコピー コマンドを使用または好みの任意のインストール パッケージに配置します。

## <a name="next-steps"></a>次の手順

- [発行ツールを使用して .NET Core アプリケーションを配置する](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Microsoft ストアのデスクトップ アプリをパッケージ化する (デスクトップ ブリッジ)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET)[.NET Framework およびアプリケーションのデプロイ](/dotnet/framework/deployment/)
