---
title: 発行または Visual Studio からクラウド サービスをデプロイするための準備 |Microsoft Docs
description: クラウドとストレージ アカウントのサービスを設定して、Azure アプリケーションを構成する手順について説明します。
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d7643d87f60b953b9c0928571036c7890e4d11f0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002979"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Visual Studio からのクラウド サービスの発行またはデプロイの準備

クラウド サービス プロジェクトを発行するには、次のサービスに設定する必要がありますこの記事で説明します。

* A**クラウド サービス**Azure 環境でロールを実行して 
* A**ストレージ アカウント**Blob、キュー、およびテーブル サービスへのアクセスを提供します。

## <a name="create-a-cloud-service"></a>クラウド サービスを作成します。

クラウド サービスでは、Azure 環境でロールを実行します。 Visual Studio で、またはを通じて、クラウド サービスを作成することができます、 [Azure portal](https://portal.azure.com/)ように、次のセクションで説明します。

### <a name="create-a-cloud-service-from-visual-studio"></a>Visual Studio からクラウド サービスを作成します。

1. 以前に作成したクラウド サービス プロジェクトでは、プロジェクトの選択を右クリックして**発行**します。
1. 必要に応じて、Microsoft または Azure サブスクリプションに関連付けられている組織のアカウントでサインインし、選択**次**に進めておく、**設定**ページ。
1. A**クラウド サービスの作成とストレージ アカウント**ダイアログが表示されます (そうでない場合は、選択**新規作成**から、**クラウド サービス**リスト)。
1. URL の一部を形成し、一意である必要がありますクラウド サービスの大文字の名前を入力します。 また、リージョンまたはアフィニティ グループを選択し、レプリケーション オプションを選択します。

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Azure ポータルでクラウド サービスを作成します。

1. [Azure Portal](https://portal.azure.com/) にサインインします。
1. 選択**Cloud Services (クラシック)** ページの左側にあります。
1. 選択 **+ 追加**、し (DNS 名、サブスクリプション、リソース グループ、および場所) に必要な情報を入力します。 後で Visual Studio でそのため、この時点でパッケージをアップロードする必要はありません。
1. 選択**作成**プロセスを完了します。

## <a name="create-a-storage-account"></a>ストレージ アカウントを作成します。

ストレージ アカウントは、Blob、キュー、およびテーブル サービスへのアクセスを提供します。 Visual Studio でのストレージ アカウントを作成する、または[Azure portal](https://portal.azure.com/)します。

### <a name="create-a-storage-account-from-visual-studio"></a>Visual Studio からストレージ アカウントを作成します。

1. **ソリューション エクスプ ローラー**以前に作成したクラウド サービス プロジェクトでは、検索、**接続済みサービス**、ロール プロジェクトを右クリックし、内のノード**接続済みサービスの追加**. (Visual Studio 2015 で右クリックし、**ストレージ**ノード**ストレージ アカウントの作成**)。
1. **接続済みサービス**一覧が表示されたら、選択**Azure Storage を使用したクラウド ストレージ**します。
1. Azure Storage ダイアログ ボックスが表示されますが、次のように選択します。 **+ 新しいストレージ アカウントの作成**、サブスクリプションの名前を指定するダイアログが表示されますアカウント、、価格レベル、リソース グループ、および場所です。
1. 選択**作成**完了したら。 新しいストレージ アカウントは、サブスクリプションで使用できるストレージ アカウントの一覧に表示されます。
1. アカウントを選択して**追加**します。

### <a name="create-a-storage-account-through-the-azure-portal"></a>Azure portal からストレージ アカウントを作成します。

1. [Azure Portal](https://portal.azure.com/) にサインインします。
1. 選択 **+ 新規**左上にします。
1. 選択**ストレージ**"Azure Marketplace で"し、**ストレージ アカウント - blob、ファイル、テーブル、キュー**右側にあるからです。
1. (名前、デプロイ モデルなど必要な情報を提供します。 です。
1. 選択**作成**プロセスを完了します。

## <a name="configure-your-app-to-use-the-storage-account"></a>ストレージ アカウントを使用するアプリを構成します。

ストレージ アカウントを作成した後は Visual Studio からの接続を自動的に Url とアクセス キーを含む、プロジェクトのサービス構成を更新します。

Visual Studio を使用してから、クラウド サービスを作成したかどうか、**接続済みサービスの追加**を開き、接続を確認できます`ServiceConfiguration.Cloud.cscfg`と`ServiceConfiguration.Local.cscfg`します。

Azure ポータルでクラウド サービスを作成した場合に同じ手順に従います[Visual Studio からストレージ アカウントの作成](#create-a-storage-account-from-visual-studio)しますが、既存のアカウントではなく新しいハブを作成します。 Visual Studio は、構成を更新します。

構成する設定を手動でページを使用してプロパティ Visual Studio でクラウド サービス プロジェクトで、該当するロールの (ロールを右クリックして**プロパティ**)。 詳細については、次を参照してください。[ストレージ アカウントへの接続文字列を構成する](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account)します。

### <a name="about-access-keys"></a>アクセス キーについて

Azure portal、Azure ストレージ サービスとも、アカウントのプライマリおよびセカンダリ アクセス キーの各リソースへのアクセスに使用できる Url が表示されます。 これらのキーを使用して、ストレージ サービスに対して行われた要求を認証します。

セカンダリ アクセス キーは、プライマリ アクセス キーとして、ストレージ アカウントへのアクセスを提供し、プライマリ アクセス キーを侵害する必要がありますバックアップとして生成されます。 さらに、定期的に、アクセス キーを再生成することをお勧めします。 セカンダリ キーを再生成中に再生成された主キーを使用するように変更することができ、主キーを再生成中にセカンダリ キーを使用する接続文字列の設定を変更することができます。

## <a name="next-steps"></a>次の手順

Visual Studio から azure についての詳細については、アプリを発行しては、次を参照してください。 [Azure ツールを使用してクラウド サービスの発行](vs-azure-tools-publishing-a-cloud-service.md)します。
