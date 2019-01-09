---
title: 配置機能のツアー
description: Visual Studio からアプリを配置する際の選択肢について説明します。
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
ms.openlocfilehash: 79cdab9ef8cd127b54117188c9d1a49ad4948c9e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53805160"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>クイック スタート: Visual Studio での配置の概要

他のコンピューター、デバイス、サーバー、クラウドにインストールする目的でアプリケーション、サービス、またはコンポーネントを配布する手法として配置が行われます。 必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。 (コマンド ラインによる配置や NuGet など、その他の配置ツールに対応しているアプリの種類はたくさんありますが、それらのツールについてはここでは触れていません。)

詳細な配置手順については、クイックスタートとチュートリアルをご覧ください。 配置オプションの概要については、「[状況に適した発行オプション](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)」を参照してください。

## <a name="deploy-to-local-folder"></a>ローカル フォルダーに配置する

ローカル フォルダーへの配置は通常、テスト目的で使用されます。あるいは、最終的な配置に別のツールを使用する段階式配置を開始する目的で使用されます。

- **ASP.NET**、**ASP.NET Core**、**Node.js**、**Python**、.**NET Core**:発行ツールを使用して、ローカル フォルダーに配置します。 利用できるオプションは厳密にはアプリの種類によって異なります。 ソリューション エクスプローラーで、プロジェクトを右クリックし、**[発行]** を選択します。 (発行プロファイルを以前に構成している場合、**[新しいプロファイルの作成]** をクリックする必要があります。)次に **[フォルダー]** を選択します。 詳細については、「[ローカル フォルダーに配置する](quickstart-deploy-to-local-folder.md)」を参照してください

    ![[発行] を選択する](../deployment/media/quickstart-publish.png)

- **Visual C++ ランタイム**:ローカル配置または静的リンクを利用して、Visual C++ ランタイムを配置できます。 詳細については、「[ネイティブ デスクトップ アプリケーションの配置 (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)」を参照してください。

## <a name="publish-to-azure"></a>Azure に発行する

- **ASP.NET**、**ASP.NET Core**、**Python**、**Node.js**:発行ツールを使用し、Azure App Service または Azure 仮想マシンにアプリを簡単に配置できます。 ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 (発行プロファイルを以前に構成している場合、**[新しいプロファイルの作成]** をクリックする必要があります。)[発行] ダイアログ ボックスで、**[App Service]** または **[Azure Virtual Machines]** を選択し、構成手順に従います。

    ![Azure App Service を選択する](../deployment/media/quickstart-publish-azure.png "Azure App Service を選択する")

    Visual Studio 2017 バージョン 15.7 以降で、ASP.NET Core アプリを **Linux 用 App Service** に配置できます。

    Python アプリについては、[Python で Azure App Service に発行する](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)方法に関するページも参照してください。

    概要については、[Azure に発行する方法](quickstart-deploy-to-azure.md)に関するページと [Linux に発行する方法](quickstart-deploy-to-linux.md)に関するページを参照してください。 [Azure に ASP.NET Core アプリを発行する](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)方法に関するページも参照してください。 Git を使用した配置については、[Git を使用して Azure に ASP.NET Core を継続的に配置する](/aspnet/core/publishing/azure-continuous-deployment)方法に関するページを参照してください。

    Azure App Service から Visual Studio に発行プロファイルをインポートする方法については、[発行設定のインポートと Azure へのデプロイ](../deployment/tutorial-import-publish-settings-azure.md)に関するページを参照してください。

    > [!NOTE]
    > Azure アカウントをお持ちでない場合、[こちらから新規登録](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)できます。

## <a name="publish-to-web-or-deploy-to-network-share"></a>Web に発行するか、ネットワーク共有に配置する

- **ASP.NET**、**ASP.NET Core**、**Node.js**、**Python**:発行ツールを使用することで、FTP または Web 配置を使って Web サイトに配置できます。 詳細については、[Web サイトに配置する](quickstart-deploy-to-a-web-site.md)方法に関するページを参照してください。

    ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。 (発行プロファイルを以前に構成している場合、**[新しいプロファイルの作成]** をクリックする必要があります。)発行ツールで、必要なオプションを選択し、構成手順に従います。

    ![IIS や FTP などを選択します。](../deployment/media/quickstart-publish-iis-ftp.png)

    Visual Studio に発行プロファイルをインポートする方法については、[発行設定のインポートと IIS への配置](../deployment/tutorial-import-publish-settings-iis.md)に関するページを参照してください。

    ASP.NET のアプリケーションとサービスは他にもさまざまな方法で配置できます。 詳細については、[ASP.NET の Web アプリケーション/サービスを配置する](http://www.asp.net/aspnet/overview/deployment)方法に関するページをご覧ください。

- **Visual C++ ランタイム**:集中配置を使用して Visual C++ ランタイムを配置できます。 詳細については、「[ネイティブ デスクトップ アプリケーションの配置 (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp)」を参照してください。

- **Windows デスクトップ**: ClickOnce 配置を使用し、Web サーバーまたはネットワーク ファイル共有に Windows デスクトップ アプリケーションを発行できます。 その後、ユーザーはシングル クリックでアプリケーションをインストールできます。 詳細については、[ClickOnce でデスクトップ アプリを配置する](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)方法に関するページと [ClickOnce でネイティブ アプリを配置する](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)方法に関するページを参照してください。

## <a name="publish-to-microsoft-store"></a>Microsoft Store に発行する

Visual Studio から、Microsoft Store に配置するためのアプリ パッケージを作成できます。

- **UWP**:アプリをパッケージ化し、メニュー項目を使用してそれを配置できます。 詳細については、[Visual Studio を使用して UWP アプリをパッケージ化する](/windows/uwp/packaging/packaging-uwp-apps)方法に関するページをご覧ください。

    ![アプリ パッケージの作成](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows デスクトップ**:Visual Studio 2017 バージョン 15.4 以降では、デスクトップ ブリッジを使用して Microsoft Store に配置できます。 これを行うには、まず Windows アプリケーション パッケージ プロジェクトを作成します。 詳細については、「[Package a desktop app for Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)」(Microsoft ストアのデスクトップ アプリをパッケージ化する (デスクトップ ブリッジ)) を参照してください。

    ![デスクトップ ブリッジ](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>デバイスに配置する (UWP)

デバイスでテストする目的で UWP アプリを配置する場合、[Visual Studio からリモート コンピューター上で UWP アプリを実行する](../debugger/run-windows-store-apps-on-a-remote-machine.md)方法に関するページを参照してください。

## <a name="create-an-installer-package-windows-client"></a>インストーラー パッケージを作成する (Windows クライアント)

デスクトップ アプリケーションを [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) でできることよりも複雑な方法でインストールする必要がある場合、インストーラー パッケージ、セットアップ プロジェクト、またはカスタム ブートストラップを作成できます。

- MSI ベースの WiX インストーラーを [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) を使用して作成できます。

- Flexera Software の [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) を Visual Studio 2017 と共に使用することも場合によっては可能です (Community Edition はサポートされていません)。 InstallShield Limited Edition は現在 Visual Studio に付属しておらず、Visual Studio 2017 でサポートされていません。今後の可用性については、[Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) にお問い合わせください。

- セットアップ プロジェクト (vdproj) を作成する場合、[Visual Studio 2017 Installer Projects 拡張](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)をインストールしてください。

- ブートストラップと呼ばれる一般的なインストーラーを構成すると、デスクトップ アプリケーションの必須コンポーネントをインストールできます。 詳細については、「[Application Deployment Prerequisites](../deployment/application-deployment-prerequisites.md)」 (アプリケーション配置の必要条件) を参照してください。

## <a name="deploy-to-test-lab"></a>テスト ラボに配置する

アプリケーションを仮想環境に配置することで、より高度な開発と試験が可能になります。 詳細については、[ラボ環境のテスト](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)に関するページを参照してください。

## <a name="devops-deployment"></a>DevOps 配置

チーム環境では、Azure Pipelines を使用し、アプリの継続的配置を有効にできます。 詳細については、[Azure Pipelines](/azure/devops/pipelines/index?view=vsts) に関するページと [Azure に配置する](/azure/devops/deploy-azure/index?view=vsts)方法に関するページを参照してください。

## <a name="deployment-for-other-app-types"></a>他の種類のアプリを配置する

| アプリの種類 | 配置シナリオ | リンク |
| --- | --- | --- |
| **Office アプリ** | Visual Studio から Office 用のアドインを発行できます。 | [Office アドインを配置し、発行する](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF または OData サービス** | Web サーバーに配置した WCF RIA サービスを他のアプリケーションで使用できます。 | [WCF Data Services の開発と配置](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch は現在 Visual Studio 2017 ではサポートされていませんが、引き続き Visual Studio 2015 以前から配置できます。 | [LightSwitch アプリケーションの配置](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>次の手順

このチュートリアルでは、さまざまなアプリケーションの配置オプションを簡単に見てきました。

> [!div class="nextstepaction"]
> [状況に適した発行オプション](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
