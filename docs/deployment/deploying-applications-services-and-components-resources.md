---
title: 展開の概要 - Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d5b15af932f8d796a27dfc060128617816b9234
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232174"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Visual Studio でのデプロイの概要

アプリケーション、サービス、またはコンポーネントを配置すると、他のコンピューターのデバイス、サーバー、またはクラウドに対してインストールするために、それらを配布することになります。 必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。

多くの一般的なアプリ タイプには、Visual Studio でソリューション エクスプ ローラーから右へ、アプリケーションをデプロイできます。 この機能のクイック ツアーは、次を参照してください。[展開でのはじめ](../deployment/deploying-applications-services-and-components.md)します。

![公開オプションを選択します。](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>状況に適した発行オプション

Visual Studio で、アプリケーションに発行できる直接、次のターゲット。

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [ファイル システム](#file-system)
- [カスタム ターゲット (IIS、FTP など)](#custom-targets) (任意の Web サーバーをすべて含みます)

**[発行]** タブでは、既存の発行プロファイルを選んだり、既存の発行プロファイルをインポートしたり、ここで説明するオプションを使って新しい発行プロファイルを作成したりできます。 IDE でのアプリの種類別の発行オプションについては、[デプロイの概要](../deployment/deploying-applications-services-and-components.md)に関する記事を参照してください。

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview)と[App Service on Linux](/azure/app-service/containers/app-service-linux-intro)インフラストラクチャを保守しなくても、さまざまなスケーラブルな web アプリケーションとサービスをすばやく作成する開発者を支援します。

選択して、コンピューティング能力を App Service を決定する、[価格レベルまたはプラン](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)含む App service。 した複数の Web アプリ (およびその他のアプリの種類) は、価格レベルを変更することがなく、同じ App Service を共有します。 たとえば、同じ App Service で Web アプリを開発、ステージング、および運用環境をホストできます。

App Service は Azure のクラウドでホストされる仮想マシン上で実行されますが、これらの仮想マシンはユーザーが管理します。 App Service では、各アプリが割り当てられます一意\*。 azurewebsites.net の URL は、サイトへのカスタム ドメイン名の割り当てを許可するすべての価格レベル Free 以外。

### <a name="when-to-choose-azure-app-service"></a>Azure App Service を選ぶ状況

- インターネット経由でアクセスできる Web アプリケーションをデプロイしたい。
- 再デプロイする必要なしに、需要に応じて Web アプリケーションを自動的に拡張したい。
- サーバーのインフラストラクチャを管理したくない (すべてのソフトウェアの更新を含む)。
- Web アプリケーションをホストするサーバーで、コンピューター レベルのカスタマイズを行う必要がない。

> 自社のデータセンターまたは他のオンプレミス コンピューターで Azure App Service を使いたい場合は、[Azure Stack](https://azure.microsoft.com/overview/azure-stack/) を使って行うことができます。

App Service への発行の詳細については、次を参照してください。[クイック スタート - Azure App Service に発行](quickstart-deploy-to-azure.md)と[クイック スタート - Linux への ASP.NET Core の発行](quickstart-deploy-to-linux.md)します。

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) を使うと、任意の数のコンピューティング リソースをクラウドに作成して管理できます。 すべてのソフトウェアと、Vm 上で更新プログラムの責任を負うをカスタマイズできることと、アプリケーションで必要なだけです。 また、ユーザーはリモート デスクトップを介して仮想マシンに直接アクセスでき、各マシンは必要な限り割り当てられた IP アドレスを保持します。

仮想マシンでホストされているアプリケーションをスケーリングするには、需要に応じた追加 Vm のスピンアップと、必要なソフトウェアを展開する必要があります。 このような制御レベルの追加により、グローバル リージョンごとに拡張方法を変えることができます。 たとえば、異なるリージョンの従業員がアプリケーションを利用している場合、リージョンの従業員の数に従って VM を拡張でき、コストを削減できる可能性があります。

詳しくは、Visual Studio の [カスタム] オプションを使ってデプロイ ターゲットとして使うことができる Azure App Service、Azure Virtual Machines、他の Azure サービスの間の[詳細な違い](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/)をご覧ください。

### <a name="when-to-choose-azure-app-virtual-machines"></a>Azure Virtual Machines を選ぶ状況

- インターネット経由でアクセス可能な Web アプリケーションをデプロイし、割り当てられた IP アドレスの有効期間全体を通して完全に制御したい。
- 専用データベース システムなどの追加ソフトウェア、特定のネットワーク構成、ディスク パーティションなど、サーバーでコンピューター レベルのカスタマイズが必要である。
- Web アプリケーションのスケーリングをきめ細かく制御したい。
- その他の理由で、アプリケーションをホストするサーバーに直接アクセスする必要がある。

> 自社のデータセンターまたは他のオンプレミス コンピューターで Azure Virtual Machines を使いたい場合は、[Azure Stack](https://azure.microsoft.com/overview/azure-stack/) を使って行うことができます。

## <a name="file-system"></a>ファイル システム

単に、アプリケーションのファイルを自分のコンピューターに特定のフォルダーにコピーするのには意味ファイル システムにデプロイします。 テスト目的で、またはコンピューターをサーバーを実行している場合、ユーザーの数の制限が使用するためにアプリケーションをデプロイする最もよく使用されます。 ターゲット フォルダーがネットワークで共有されている場合、ファイル システムにデプロイすると、他のユーザーも Web アプリケーション ファイルを使用して特定のサーバーにデプロイできます。

すべてのローカル コンピューター、サーバーを実行しているアプリケーションをインターネットまたはイントラネットの構成方法に応じてとが接続されているネットワークで使用できる作成できます。 (コンピューターがインターネットに直接接続されている場合、外部のセキュリティ脅威からの保護に特に注意が必要です)。ユーザーは、これらのコンピューターを管理するので、ソフトウェアとハードウェアの構成を完全に制御できます。

何らかの理由で (コンピューターのアクセスなど) ユーザーが Azure App Service や Azure Virtual Machines などのクラウド サービスを使用できない場合、ユーザーは自社のデータセンターで [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) を使用できます。 Azure Stack を使うと、ユーザーは Azure App Service および Azure Virtual Machines によってコンピューティング リソースを管理および使用しながら、すべてのものをオンプレミスに保持できます。

### <a name="when-to-choose-file-system-deployment"></a>ファイル システムのデプロイを選ぶ状況

- ファイル共有にアプリケーションをデプロイし、他のユーザーがそれを別のサーバーにデプロイすることだけが必要である。
- ローカル テスト デプロイのみが必要である。
- 別のデプロイ ターゲットに送る前にアプリケーション ファイルを調べて場合によっては個別に変更したい。

詳細については、次を参照してください[クイック スタート - ローカル フォルダーに配置する。](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>カスタム ターゲット (IIS、FTP)

カスタム ターゲットを使用して、Azure App Service、Azure Virtual Machines、またはローカル ファイル システム以外のターゲットにアプリケーションを配置できます。 アクセスできるファイル システムや他のサーバー (インターネットまたはイントラネット) にデプロイできます。他のクラウド サービスも含まれます。 Web デプロイ (ファイルまたは .ZIP) および FTP で使用できます。

カスタム ターゲットを選ぶと、Visual Studio はユーザーにプロファイル名の指定を求めた後、ターゲット サーバーまたは場所、サイト名、資格情報などの追加の**接続**情報を収集します。 **[設定]** タブで次のビヘイビアーをコントロールできます。

- デプロイする構成。
- 宛先から既存のファイルを削除するかどうか。
- 発行中にプリコンパイルするかどうか。
- App_Data フォルダーのファイルをデプロイから除外するかどうか。

Visual Studio では任意の数のカスタム デプロイ プロファイルを作成し、異なる設定でプロファイルを管理できます。

### <a name="when-to-choose-custom-deployment"></a>カスタム デプロイを選ぶ状況

- URL でアクセスできる Azure 以外のプロバイダーでクラウド サービスを使っている。
- Visual Studio で使っている資格情報または Azure アカウントに直接結び付けられている資格情報とは異なる資格情報を使ってデプロイしたい。
- デプロイするたびに、ターゲットからファイルを削除したい。

詳細については、次を参照してください[クイック スタート - web サイトに展開する。](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>次の手順

チュートリアル:

- [発行ツールを使用する .NET Core アプリケーションをデプロイします。](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [ASP.NET core アプリを Azure に発行します。](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ での配置](/cpp/ide/deployment-in-visual-cpp)
- [UWP アプリを展開します。](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Web Deploy を使用して Azure に Node.js アプリを発行します。](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure App Service への Python アプリを発行します。](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
