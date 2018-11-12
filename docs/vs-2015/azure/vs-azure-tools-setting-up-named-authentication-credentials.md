---
title: 名前付き認証資格情報設定 |Microsoft Docs
description: Visual Studio を使用して Visual Studio から Azure へのアプリケーションを発行するか、既存のクラウド サービスを監視することができますので、Azure への要求を認証する資格情報を提供する方法について説明します。
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002912"
---
# <a name="set-up-named-authentication-credentials"></a>名前付き認証資格情報の設定

Azure にアプリケーションを公開する、または既存のクラウド サービスを監視するには、Visual Studio には、つまり、Azure サブスクリプション ID と 2048 ビット以上のキーには、有効な X.509 v3 証明書を Azure に要求を認証する資格情報が必要です。 これらの資格情報を次のいずれかを指定します。

- Visual Studio を選択します**ビュー > サーバー エクスプ ローラー**を右クリックし、 **Azure**ノードの  **Microsoft Azure サブスクリプションへの接続**、サインインします。
- サブスクリプション ファイルの作成 (`.publishsettings`)、証明書の公開キーが含まれています。 サブスクリプション ファイルには、この記事で説明されている 1 つ以上のサブスクリプションの資格情報を含めることができます。

注: これらの資格情報は Azure ストレージ サービスに対する要求の認証に使用される資格情報によって異なります。

## <a name="create-a-subscription-file"></a>サブスクリプション ファイルを作成します。

サーバー エクスプ ローラーで右クリックし、 **Azure**ノード**フィルター サブスクリプションの管理および**します。 選択し、**証明書**タブをクリックし、次の操作のいずれかの操作を行います。

- 選択**インポート**を開く、 **Microsoft Azure サブスクリプションのインポート** ダイアログ ボックス。 選択、**サブスクリプション ファイルのダウンロード**リンク、およびブラウザーでは、一時的な場所にダウンロードしたファイルを保存します。 ダイアログ ボックスに戻りますダウンロード場所を参照し、認証で使用するためにインポートします。
- アクティブなサブスクリプションを選択し、選択**編集**認証で使用するための既存のサブスクリプションを編集するためのダイアログを開きます。
- 選択**新規**を開く、**新しいサブスクリプション** ダイアログ ボックスし、必要な情報を提供します。 ダイアログ ボックスに、クラウドに、証明書をアップロードするサービスが記載されている Azure portal にサインイン、select、クラウド サービスに移動します**設定 > 管理証明書**を選択します**アップロード**、し、パスを指定、`.cer`ファイル。

証明書を自分で作成する場合は、ことができます」の手順を参照してください。[の作成と管理は、Azure の証明書のアップロード](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx)に証明書を手動でアップロード、 [Azure portal](https://portal.azure.com/)します。

## <a name="next-steps"></a>次の手順

- [Web Apps の概要](https://docs.microsoft.com/azure/app-service/)
- [Azure App Service へのアプリをデプロイします。](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Visual Studio を使用して WebJobs をデプロイします。](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [作成し、クラウド サービスのデプロイ](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)