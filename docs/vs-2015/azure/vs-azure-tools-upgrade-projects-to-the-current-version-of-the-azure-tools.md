---
title: 現在のバージョンの Azure tools にプロジェクトをアップグレードする方法 |Microsoft Docs
description: Visual Studio で Azure プロジェクトを Azure tools の現在のバージョンにアップグレードする方法について説明します
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c5fb70f2dd09338dd2e2f6b01cb60bf2be0cdbdd
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002909"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>現行バージョンの Azure Tools for Visual Studio にプロジェクトをアップグレードする方法
## <a name="overview"></a>概要
Azure ツール (または 1.6 より以前のリリース) の現在のリリースをインストールすると、Azure ツールを使用して作成されたすべてのプロジェクトを 1.6 する前にリリース (2011 年 11 月) は、メッセージを開くとすぐに自動的にアップグレードします。 これらのツール 1.6 (2011 年 11 月) リリースを使用してプロジェクトを作成し、そのリリースをインストールしている、まだ場合、は、以前のリリースでは、これらのプロジェクトを開き、後でそれらをアップグレードするかどうか。

## <a name="how-your-project-changes-when-you-upgrade-it"></a>アップグレードするときに、プロジェクトを変更する方法
プロジェクトが自動的にアップグレードまたはアップグレードすることを指定する、特定のアセンブリの現在のバージョンを使用するプロジェクトを変更し、このセクションの説明に従って、一部のプロパティが変更もします。 プロジェクトには、新しいバージョンのツールと互換性があるその他の変更が必要とする場合は、これらの変更を手動で行う必要があります。

* 新しいバージョンの Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitoirTraceListener.dll を参照するには、web ロールの web.config ファイルと worker ロールの app.config ファイルが更新されます。
* Microsoft.WindowsAzure.StorageClient.dll、Microsoft.WindowsAzure.Diagnostics.dll、Microsoft.WindowsAzure.ServiceRuntime.dll の各アセンブリは、新しいバージョンにアップグレードされます。
* Azure のプロジェクト ファイル (.ccproj) に格納された発行プロファイルが .azurepubxml という拡張子を別のファイルにで移動、**発行**サブディレクトリ。
* 発行プロファイルの一部のプロパティは、追加または変更された機能をサポートするために更新されます。 **AllowUpgrade**は置き換え **[deploymentreplacementmethod]** のため同時にまたは段階的にデプロイしたクラウド サービスを更新することができます。
* プロパティ**UseIISExpressByDefault**が追加され、false に設定されるのでのデバッグに使用する web サーバーが IIS Express にインターネット インフォメーション サービス (IIS) を自動的に変更はありません。 IIS Express は、ツールのそれ以降のリリースで作成されたプロジェクトの既定の web サーバーです。
* Azure Caching は、1 つ以上のプロジェクトのロールでホストされる、サービスの構成 (.cscfg ファイル) とサービス定義 (.csdef ファイル) の一部のプロパティは、プロジェクトをアップグレードするときに変更されます。 プロジェクトは、Azure Caching NuGet パッケージを使用している場合は、プロジェクトがパッケージの最新バージョンにアップグレードされます。 Web.config ファイルを開いて、アップグレード処理中に、クライアントの構成が正しく維持されていることを確認する必要があります。 NuGet パッケージを使用せず、Azure の Caching クライアント アセンブリへの参照を追加した場合は、これらのアセンブリが更新されません。これらの参照を新しいバージョンに手動で更新する必要があります。

> [!IMPORTANT]
> F#プロジェクトでは、これらのアセンブリの新しいバージョンを参照するよう、Azure アセンブリへの参照を手動で更新する必要があります。
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Azure プロジェクトを現在のリリースにアップグレードする方法
1. アップグレードされたプロジェクトで使用する Visual Studio のインストール時に Azure Tools の現在のバージョンをインストールしにアップグレードするプロジェクトを開きます。 Azure ツールを使用して、プロジェクトが作成された場合 1.6 する前にリリース (2011 年 11 月)、プロジェクトは、現在のバージョンにアップグレード自動的にします。 プロジェクトが作成された場合、2011 年 11 月のリリースしリリースがまだインストールされている、そのリリースで、プロジェクトが開きます。
2. ソリューション エクスプ ローラーでプロジェクト ノードのショートカット メニューを開き、選択**プロパティ**を選択し、**アプリケーション**表示されるダイアログ ボックスのタブ。
   
    **アプリケーション** タブには、プロジェクトに関連付けられたツール バージョンが表示されます。 Azure Tools の現在のバージョンが表示されている場合、プロジェクト既にアップグレードされました。 タブに表示より新しいバージョンのツールをインストールした場合、**アップグレード**ボタンが表示されます。
3. 選択、**アップグレード**ツールの現在のバージョンにプロジェクトをアップグレードするボタンをクリックします。
4. プロジェクトをビルドし、API の変更に起因するエラーを解決します。 新しいバージョンのコードを変更する方法については、特定の API のドキュメントを参照してください。

