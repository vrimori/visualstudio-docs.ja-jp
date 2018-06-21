---
title: 配置機能のツアー
description: Visual Studio からアプリを展開するためのオプションについて説明します。
ms.custom: mvc
ms.date: 11/26/2017
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
ms.openlocfilehash: 8d2c84b8e5d37876d890d40144b281e236fdcd0c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766312"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>クイック スタート: まず、Visual Studio での展開

アプリケーション、サービス、またはコンポーネントを配置すると、他のコンピューターのデバイス、サーバー、またはクラウドに対してインストールするために、それらを配布することになります。 必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。 (多くの種類のアプリは、ここで説明されていない他の展開ツール コマンド ライン デプロイ NuGet などをサポートします)。

ステップ バイ ステップ デプロイメントの手順のチュートリアルを参照してください。 Web アプリケーションを配置する場合は、Visual Studio から最適な展開オプションを決定するために、より詳細な情報 [状況に適した発行オプション](../ide/not-in-toc/web-publish-options.md) を参照してください。

## <a name="deploy-to-local-folder"></a>ローカル フォルダーに配置します。

ローカル フォルダーへの展開は通常、テスト用または段階的なデプロイメントを別のツールを使用して、最終的な配置を開始するに使用されます。

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、 **Python**、および **。NET コア**: 発行ツールを使用して、ローカル フォルダーに配置します。 利用可能なオプションは、アプリの種類によって異なります。 ソリューション エクスプ ローラーでプロジェクトを右クリックして選択**発行**です。 (任意の発行プロファイルを構成していない場合をクリックし、**新しいプロファイルを作成**)。次に、選択**フォルダー**です。 詳細については、次を参照してください。[をローカル フォルダーに配置](quickstart-deploy-to-local-folder.md)です。

    ![選択を発行](../deployment/media/quickstart-publish.png)

- **Visual C ランタイム**: ローカル配置または静的リンクを使用して、Visual C ランタイムを配置することができます。 詳細については、次を参照してください。[ネイティブ デスクトップ アプリケーションの配置 (Visual c)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)です。 

## <a name="azure"></a> Azure に発行します。

- **ASP.NET**、 **ASP.NET Core**、 **Python**、および**Node.js**: 発行ツールを使用するには Azure App Service と Azure 仮想にアプリを迅速に配置するにはマシンです。 ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 (任意の発行プロファイルを構成していない場合をクリックし、**新しいプロファイルを作成**)。[発行] ダイアログ ボックスでいずれかを選択**App Service**または**Azure Virtual Machines**、し構成手順に従います。

    ![Azure App Service の選択](../deployment/media/quickstart-publish-azure.png "Azure App Service の選択")

    Visual Studio 2017 バージョン 15.7 を ASP.NET Core アプリケーションを展開できます**for Linux の App Service**です。

    Azure App Service からの発行プロファイルを Visual Studio にインポートする方法の詳細については、次を参照してください。[発行設定をインポートし、Azure にデプロイ](../deployment/tutorial-import-publish-settings-azure.md)です。

    概要については、次を参照してください。 [Publish to Azure](quickstart-deploy-to-azure.md)です。 またを参照してください[ASP.NET Core アプリケーションを Azure に公開](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)です。 Git を使用して展開では、次を参照してください。 [Git を使用した Azure への ASP.NET Core の継続的なデプロイ](/aspnet/core/publishing/azure-continuous-deployment)です。

    > [!NOTE]
    > Azure アカウントをもっていない場合は、ここから [サインアップ](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio) することができます。

## <a name="web"></a> Web に発行またはネットワーク共有に展開

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、および**Python**: FTP や Web Deploy を使用して web サイトを展開する、発行ツールを使用することができます。 詳細については、次を参照してください。 [web サイトへのデプロイ](quickstart-deploy-to-a-web-site.md)です。

    ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 (任意の発行プロファイルを構成していない場合をクリックし、**新しいプロファイルを作成**)。ツールでは、発行には、構成手順を実行してオプションを選択します。

    ![IIS、FTP などを選択します。](../deployment/media/quickstart-publish-iis-ftp.png)

    Visual Studio での発行プロファイルをインポートする方法については、次を参照してください。[発行の設定をインポートし、IIS に展開](../deployment/tutorial-import-publish-settings-iis.md)です。

    いくつかの他の方法で ASP.NET アプリケーションとサービスを展開することもできます。 詳細については、次を参照してください。[を展開する ASP.NET web アプリケーションとサービス](http://www.asp.net/aspnet/overview/deployment)です。

- **Visual C ランタイム**: 集中配置を使用して、Visual C ランタイムを配置することができます。 詳細については、次を参照してください。[ネイティブ デスクトップ アプリケーションの配置 (Visual c)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)です。 

- **Windows デスクトップ**web サーバーまたは ClickOnce 配置を使用してネットワーク ファイル共有に、Windows デスクトップ アプリケーションを発行することができます。 その後、ユーザーはシングル クリックでアプリケーションをインストールできます。 詳細については、次を参照してください。 [ClickOnce を使用して、デスクトップ アプリを展開](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)と[ClickOnce を使用してネイティブ アプリを展開](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)です。

## <a name="microsoft_store"></a> Microsoft Store に公開します。

Visual studio では、Microsoft ストアへの展開用のアプリ パッケージを作成できます。

- **UWP**: アプリをパッケージ化して、メニュー項目を使用して展開することができます。 詳細については、次を参照してください。 [Visual Studio を使用して、UWP アプリをパッケージ化](/windows/uwp/packaging/packaging-uwp-apps)です。

    ![アプリ パッケージの作成](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows デスクトップ**: 以降では、Visual Studio 2017 バージョン 15.4 デスクトップ ブリッジを使用して Microsoft ストアに配置することができます。 これを行うには、まず、Windows アプリケーション パッケージのプロジェクトを作成します。 詳細については、次を参照してください。 [Microsoft ストア (デスクトップ ブリッジ) のデスクトップ アプリをパッケージ化](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)です。

    ![デスクトップのブリッジ](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>デバイス (UWP) への配置します。

デバイス上でのテスト、UWP アプリを展開する場合は、次を参照してください。 [Visual Studio でのリモート コンピューター上の実行の UWP アプリ](../debugger/run-windows-store-apps-on-a-remote-machine.md)です。

## <a name="installer"></a> インストーラー パッケージ (Windows クライアント) を作成します。

かどうか必要よりよりもデスクトップ アプリケーションの複雑なインストール[ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)提供可能なインストーラー パッケージ、セットアップ プロジェクトまたはカスタム ブートス トラップを作成することができます。

- MSI ベース WiX インストーラーを使用して作成することができます、 [WiX ツールセット Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)です。

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera ソフトウェアからは、Visual Studio 2017 (Community Edition はサポートされていません) で使用可能性があります。 InstallShield Limited Edition は Visual Studio に付属しなくと Visual Studio 2017; でサポートされていないことに注意してください。かどうかを[Flexera ソフトウェア](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)将来可能かどうか。

- セットアップ プロジェクト (vdproj) を作成する場合は、インストール、 [Visual Studio 2017 Installer Projects extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)です。

- ブートス トラップと呼ばれる一般的なインストーラーを構成することによって、デスクトップ アプリケーションに必要なコンポーネントをインストールできます。 詳細については、次を参照してください。[アプリケーション展開の前提条件](../deployment/application-deployment-prerequisites.md)です。

## <a name="deploy-to-test-lab"></a>テスト ラボに配置します。

高度な開発と、仮想環境にアプリケーションを展開することでテストを有効にすることができます。 詳細については、次を参照してください。[ラボ環境でテスト](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)です。

## <a name="devops-deployment"></a>DevOps の展開

チームの環境でアプリの継続的なデプロイを有効にするのに Visual Studio Team Services (VSTS) を使用することができます。 詳細については、次を参照してください。[ビルドとリリースの](/vsts/build-release/index)と[Azure へのデプロイ](/vsts/deploy-azure/index)です。

## <a name="deployment-for-other-app-types"></a>その他の種類のアプリの展開

| アプリの種類 | 配置シナリオ | リンク |
| --- | --- | --- |
| **Office アプリ** | Visual Studio での Office 用アドインを発行できます。 | [展開し、Office アドインの公開](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF サービスまたは OData サービス**  | その他のアプリケーションでは、web サーバーに配置した WCF RIA サービスを使用できます。 | [開発と WCF Data Services の配置](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch では、Visual Studio 2017 は不要になったサポートされますが、Visual Studio 2015 から、以前にも展開できます。 | [LightSwitch アプリケーションの配置](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>次の手順

このチュートリアルでは、さまざまなアプリケーションの配置オプションを簡単に見てかかりました。 ASP.NET などの web アプリケーションを展開する場合は、Visual Studio で使用できる配置オプションの一部についてさらに詳しい情報を読み取る。

> [!div class="nextstepaction"]
> [どのような発行オプションは、私のですか。](../ide/not-in-toc/web-publish-options.md)

