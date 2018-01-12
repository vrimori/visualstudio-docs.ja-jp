---
title: "展開の概要 - Visual Studio |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e05bf361515b45f3ebc7683fa0c83ec6116d9419
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="deployment-overview-in-visual-studio"></a>Visual Studio での配置の概要

アプリケーション、サービス、またはコンポーネントを配置すると、他のコンピューターのデバイス、サーバー、またはクラウドに対してインストールするために、それらを配布することになります。 必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。 (多くの種類のアプリは、ここで説明されていない他の展開ツール コマンド ライン デプロイ NuGet などをサポートします)。

詳しい手順については、チュートリアルを参照してください。

### <a name="deploy-to-local-folder"></a>ローカル フォルダーに配置します。

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、 **Python**、および**.NET Core**: 発行ツールを使用してローカルに展開するにはフォルダーです。 利用可能なオプションは、アプリの種類によって異なります。 ソリューション エクスプ ローラーでプロジェクトを右クリックして選択**発行**を選択し**フォルダー**です。 詳細については、次を参照してください。[をローカル フォルダーに配置](quickstart-deploy-to-local-folder.md)です。

    ![選択を発行](../deployment/media/quickstart-publish.png)

- **Visual C ランタイム**: ローカル配置または静的リンクを使用して、Visual C ランタイムを配置することができます。 詳細については、次を参照してください。[ネイティブ デスクトップ アプリケーションの配置 (Visual c)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)です。 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Web に発行またはネットワーク共有に展開

- **ASP.NET**、 **ASP.NET Core**、 **Node.js**、 **Python**、および**.NET Core**: を展開する、発行ツールを使用することができます、web サイトの FTP や Web Deploy を使用します。 詳細については、次を参照してください。 [web サイトへのデプロイ](quickstart-deploy-to-a-web-site.md)です。

    ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 ツールでは、発行には、構成手順を実行してオプションを選択します。

    ![IIS、FTP などを選択します。](../deployment/media/quickstart-publish-iis-ftp.png)

    いくつかの他の方法で ASP.NET アプリケーションとサービスを展開することもできます。 詳細については、次を参照してください。[を展開する ASP.NET web アプリケーションとサービス](http://www.asp.net/aspnet/overview/deployment)です。

- **Visual C ランタイム**: 集中配置を使用して、Visual C ランタイムを配置することができます。 詳細については、次を参照してください。[ネイティブ デスクトップ アプリケーションの配置 (Visual c)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)です。 

- **Windows デスクトップ**web サーバーまたは ClickOnce 配置を使用してネットワーク ファイル共有に、Windows デスクトップ アプリケーションを発行することができます。 その後、ユーザーはシングル クリックでアプリケーションをインストールできます。 詳細については、次を参照してください。 [ClickOnce を使用して、デスクトップ アプリを展開](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)と[ClickOnce を使用してネイティブ アプリを展開](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)です。

### <a name="publish-to-azure"></a>Azure に発行する

- **ASP.NET、ASP.NET Core、Python、Node.js、および .NET Core** web アプリケーション: アプリを Azure App Service または Azure の仮想マシンを迅速に配置する、発行ツールを使用することができます。 ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 [発行] ダイアログ ボックスでいずれかを選択**Microsoft Azure App Service**または**Microsoft Azure Virtual Machines**、し構成手順に従います。

    ![Azure App Service の選択](../deployment/media/quickstart-publish-azure.png "Azure App Service の選択")

    をパブリッシュする Azure の仮想マシンを右にスクロール、選択**Microsoft Azure Virtual Machines**です。

    概要については、次を参照してください。 [Publish to Azure](quickstart-deploy-to-azure.md)です。 またを参照してください[ASP.NET Core アプリケーションを Azure に公開](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)です。 Git を使用して展開では、次を参照してください。 [Git を使用した Azure への ASP.NET Core の継続的なデプロイ](/aspnet/core/publishing/azure-continuous-deployment)です。

    > [!NOTE]
    > Azure アカウントがない場合は[サインアップ](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)です。

- その他の**Azure サービス**: 固有の仕様を参照してください[Azure サービス](/azure/#pivot=products)Visual Studio によってサポートされる可能性があるさまざまな展開オプションをマニュアルでします。

### <a name="publish-to-microsoft-store"></a>Microsoft Store に公開します。

Visual studio では、Microsoft ストアへの展開用のアプリ パッケージを作成できます。

- **UWP**: アプリをパッケージ化して、メニュー項目を使用して展開することができます。 詳細については、次を参照してください。 [Visual Studio を使用して、UWP アプリをパッケージ化](/windows/uwp/packaging/packaging-uwp-apps)です。

    ![アプリ パッケージの作成](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows デスクトップ**: 以降では、Visual Studio 2017 バージョン 15.4 デスクトップ ブリッジを使用して Microsoft ストアに配置することができます。 これを行うには、まず、Windows アプリケーション パッケージのプロジェクトを作成します。 詳細については、次を参照してください。 [Microsoft ストア (デスクトップ ブリッジ) のデスクトップ アプリをパッケージ化](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)です。

    ![デスクトップのブリッジ](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>インストーラー パッケージ (Windows クライアント) を作成します。

- MSI ベース WiX インストーラーを使用して作成することができます、 [WiX ツールセット Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)です。

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera ソフトウェアからは、Visual Studio 2017 (Community Edition はサポートされていません) で使用可能性があります。 InstallShield Limited Edition は Visual Studio に付属しなくと Visual Studio 2017; でサポートされていないことに注意してください。かどうかを[Flexera ソフトウェア](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)将来可能かどうか。

- セットアップ プロジェクト (vdproj) を作成する場合は、インストール、 [Visual Studio 2017 Installer Projects extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)です。

- ブートス トラップと呼ばれる一般的なインストーラーを構成することによって、デスクトップ アプリケーションに必要なコンポーネントをインストールできます。 詳細については、次を参照してください。[アプリケーション展開の前提条件](../deployment/application-deployment-prerequisites.md)です。

### <a name="deploy-to-test-lab"></a>テスト ラボに配置します。

高度な開発と、仮想環境にアプリケーションを展開することでテストを有効にすることができます。 詳細については、次を参照してください。[ラボ環境でテスト](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)です。

### <a name="devops-deployment"></a>DevOps の展開

チームの環境でアプリの継続的なデプロイを有効にするのに Visual Studio Team Services (VSTS) を使用することができます。 詳細については、次を参照してください。[ビルドとリリースの](/vsts/build-release/index)と[Azure へのデプロイ](/vsts/deploy-azure/index)です。

### <a name="deployment-for-other-app-types"></a>その他の種類のアプリの展開

| アプリの種類 | 配置シナリオ | リンク |
| --- | --- | --- |
| **Office アプリ** | Visual Studio での Office 用アドインを発行できます。 | [展開し、Office アドインの公開](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF サービスまたは OData サービス**  | その他のアプリケーションでは、web サーバーに配置した WCF RIA サービスを使用できます。 | [開発と WCF Data Services の配置](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch では、Visual Studio 2017 は不要になったサポートされますが、Visual Studio 2015 から、以前にも展開できます。 | [LightSwitch アプリケーションの配置](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

