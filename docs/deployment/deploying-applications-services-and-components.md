---
title: 展開の機能ツアー
description: Visual Studio からアプリを展開するためのオプションについて説明します。
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5824876adc75430085ea0f69dc6f01be722526f5
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231227"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>クイック スタート: は、最初に、Visual Studio でのデプロイについてください。

アプリケーション、サービス、またはコンポーネントを配置することでその他のコンピューター、デバイス、またはサーバー、またはクラウドでのインストールの配布します。 必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。 (多くのアプリの種類は、ここで説明されていない他の展開ツール コマンド ライン デプロイまたは NuGet などをサポートします)。

クイック スタートおよびチュートリアル ステップ バイ ステップのデプロイの手順を参照してください。 デプロイ オプションの概要については、次を参照してください。[どのような公開オプションは私のでしょうか。](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)します。

## <a name="deploy-to-local-folder"></a>ローカル フォルダーに配置します。

ローカル フォルダーへのデプロイは通常、テスト用、または、最終的な配置の他のツールを使用する段階的展開の開始に使用されます。

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、 **Python**と **。NET Core**: 発行ツールを使用して、ローカル フォルダーに配置します。 利用可能なオプションは、アプリの種類によって異なります。 ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**発行**します。 (クリックする必要がありますし、任意の発行プロファイルが既に構成されている場合**新しいプロファイルを作成する**)。次に、選択**フォルダー**します。 詳細については、次を参照してください。[ローカル フォルダーに配置する](quickstart-deploy-to-local-folder.md)します。

    ![選択の発行](../deployment/media/quickstart-publish.png)

- **Visual C ランタイム**: ローカル デプロイまたは静的リンクを使用して Visual C のランタイムをデプロイすることができます。 詳細については、次を参照してください。[ネイティブ デスクトップ アプリケーションの配置 (Visual c)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)します。 

## <a name="publish-to-azure"></a>Azure に発行する

- **ASP.NET**、 **ASP.NET Core**、 **Python**、および**Node.js**: 発行ツールを使用して、Azure App Service または Azure 仮想アプリをすばやくデプロイするにはマシン。 ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 (クリックする必要がありますし、任意の発行プロファイルが既に構成されている場合**新しいプロファイルを作成する**)。[発行] ダイアログ ボックスで、いずれかを選択**App Service**または**Azure Virtual Machines**、構成の手順に従います。

    ![Azure App Service を選択](../deployment/media/quickstart-publish-azure.png "Azure App Service の選択")

    Visual Studio 2017 バージョン 15.7 以降では ASP.NET Core アプリを展開できます**Linux 用 App Service**します。

    Python のアプリを参照してくださいも[Python - Azure App Service への発行](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)します。

    概要については、次を参照してください。 [Publish to Azure](quickstart-deploy-to-azure.md)と[Linux への発行](quickstart-deploy-to-linux.md)します。 またを参照してください[を Azure に ASP.NET Core アプリを発行](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)します。 Git を使用して展開では、次を参照してください。 [Git を使用した Azure への ASP.NET Core の継続的なデプロイ](/aspnet/core/publishing/azure-continuous-deployment)します。

    Azure App Service から発行プロファイルを Visual Studio にインポートする方法の詳細については、次を参照してください。[発行設定をインポートし、Azure にデプロイ](../deployment/tutorial-import-publish-settings-azure.md)します。

    > [!NOTE]
    > Azure アカウントをもっていない場合は、ここから [サインアップ](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio) することができます。

## <a name="publish-to-web-or-deploy-to-network-share"></a>Web に公開するか、ネットワーク共有への展開

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、および**Python**: 発行ツールを使用して、FTP や Web Deploy を使用して web サイトにデプロイすることができます。 詳細については、次を参照してください。 [web サイトへのデプロイ](quickstart-deploy-to-a-web-site.md)します。

    ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 (クリックする必要がありますし、任意の発行プロファイルが既に構成されている場合**新しいプロファイルを作成する**)。発行ツールでは、構成手順を実行してオプションを選択します。

    ![IIS、FTP などを選択します。](../deployment/media/quickstart-publish-iis-ftp.png)

    Visual Studio での発行プロファイルをインポートする方法については、次を参照してください。[発行の設定をインポートし、IIS に配置](../deployment/tutorial-import-publish-settings-iis.md)します。

    さまざまな他の方法で ASP.NET アプリケーションとサービスをデプロイすることもできます。 詳細については、次を参照してください。[を展開する ASP.NET web アプリケーションとサービス](http://www.asp.net/aspnet/overview/deployment)します。

- **Visual C ランタイム**: 集中配置を使用して Visual C のランタイムをデプロイすることができます。 詳細については、次を参照してください。[ネイティブ デスクトップ アプリケーションの配置 (Visual c)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)します。 

- **Windows デスクトップ**web サーバーまたは ClickOnce 配置を使用してネットワーク ファイル共有を Windows デスクトップ アプリケーションを発行することができます。 その後、ユーザーはシングル クリックでアプリケーションをインストールできます。 詳細については、次を参照してください。 [ClickOnce を使用してデスクトップ アプリのデプロイ](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)と[ClickOnce を使用してネイティブ アプリのデプロイ](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)します。

## <a name="publish-to-microsoft-store"></a>Microsoft Store への公開します。

Visual studio では、Microsoft Store へのデプロイ用のアプリ パッケージを作成できます。

- **UWP**: アプリのパッケージ化し、メニュー項目を使用して、デプロイすることができます。 詳細については、次を参照してください。 [Visual Studio を使用して UWP アプリをパッケージ化](/windows/uwp/packaging/packaging-uwp-apps)します。

    ![アプリ パッケージの作成](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows デスクトップ**: Visual Studio 2017 バージョン 15.4 以降、デスクトップ ブリッジを使用して Microsoft Store に配置することができます。 これを行うには、まず、Windows アプリケーション パッケージ プロジェクトを作成します。 詳細については、次を参照してください。 [Microsoft Store (デスクトップ ブリッジ) のデスクトップ アプリをパッケージ化](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)します。

    ![デスクトップ ブリッジ](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>デバイス (UWP) への配置します。

デバイスでテスト用の UWP アプリを展開する場合は、次を参照してください。 [Visual Studio でのリモート コンピューターでの実行の UWP アプリ](../debugger/run-windows-store-apps-on-a-remote-machine.md)します。

## <a name="create-an-installer-package-windows-client"></a>インストーラー パッケージ (Windows クライアント) を作成します。

必要なかどうかはよりもデスクトップ アプリケーションの複雑なインストール[ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)インストーラー パッケージをセットアップ プロジェクト、またはカスタム ブートス トラップを作成することができますを提供できます。

- 使用して、MSI ベースの WiX インストーラを作成することができます、 [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)します。

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera software は、Visual Studio 2017 (Community Edition がサポートされていません) で使用できます。 InstallShield Limited Edition は不要になった Visual Studio に含まれているし、は、Visual Studio 2017 ではサポートされていません確認[Flexera ソフトウェア](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)将来の可用性についてです。

- セットアップ プロジェクト (vdproj) を作成する場合は、インストール、 [Visual Studio 2017 Installer Projects extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)します。

- デスクトップ アプリケーションに必要なコンポーネントをインストールするには、ブートス トラップと呼ばれる一般的なインストーラーを構成します。 詳細については、次を参照してください。[アプリケーション展開の前提条件](../deployment/application-deployment-prerequisites.md)します。

## <a name="deploy-to-test-lab"></a>テスト ラボに配置します。

高度な開発と仮想環境にアプリケーションを配置してテストを有効にすることができます。 詳細については、次を参照してください。[ラボ環境でテスト](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)します。

## <a name="devops-deployment"></a>DevOps の展開

チームの環境で Visual Studio Team Services (VSTS) を使用して、アプリの継続的なデプロイを有効にすることができます。 詳細については、次を参照してください。[ビルドとリリース](/vsts/build-release/index)と[Deploy to Azure](/vsts/deploy-azure/index)します。

## <a name="deployment-for-other-app-types"></a>その他の種類のアプリの展開

| アプリの種類 | 配置シナリオ | リンク |
| --- | --- | --- |
| **Office アプリ** | For Visual Studio からの Office アドインを発行できます。 | [展開して、Office アドインを発行](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF または OData サービス**  | その他のアプリケーションでは、web サーバーに配置した WCF RIA サービスを使用できます。 | [開発と WCF Data Services の配置](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch では、Visual Studio 2017 ではサポートされなくが、Visual Studio 2015 から、以前に引き続き展開できます。 | [LightSwitch アプリケーションの配置](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>次の手順

このチュートリアルでは、さまざまなアプリケーションの配置オプションを簡単に見てかかりました。

> [!div class="nextstepaction"]
> [どのような公開オプションは、私のでしょうか。](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
