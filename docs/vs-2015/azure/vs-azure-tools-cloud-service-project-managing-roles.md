---
title: Visual Studio を使用した Azure cloud services でロールの管理 |Microsoft Docs
description: 追加および Visual Studio を使用した Azure cloud services でロールを削除する方法について説明します。
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002889"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Visual Studio を使用した Azure cloud services でロールの管理
Azure クラウド サービスを作成した後は、新しいロールを追加またはそこから既存のロールを削除します。 既存のプロジェクトをインポートし、ロールに変換できます。 たとえば、ASP.NET web アプリケーションをインポートでき、web ロールとして指定できます。

## <a name="adding-a-role-to-an-azure-cloud-service"></a>ロールを Azure クラウド サービスを追加します。
次の手順では、web または worker ロールを Visual Studio での Azure クラウド サービス プロジェクトに追加することを説明します。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**、プロジェクト ノードを展開

1. 右クリックし、**ロール**ノード コンテキスト メニューを表示します。 コンテキスト メニューでは、次のように選択します。**追加**、現在のソリューションから、既存の web ロールまたはワーカー ロールを選択します。 または、web またはワーカー ロール プロジェクトを作成します。 ASP.NET web アプリケーション プロジェクトなどの適切なプロジェクトを選択し、ロール プロジェクトに関連付けることができますも。

    ![Azure クラウド サービス プロジェクトにロールを追加するメニュー オプション](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Azure クラウド サービスからロールを削除します。
次の手順では、Visual Studio での Azure クラウド サービス プロジェクトから web または worker ロールを削除することを説明します。

1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。

1. **ソリューション エクスプ ローラー**、プロジェクト ノードを展開

1. 展開、**ロール**ノード。

1. 削除して、コンテキスト メニューから選択するノードを右クリックして**削除**します。 

    ![Azure クラウド サービスにロールを追加するメニュー オプション](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Azure クラウド サービス プロジェクトにロールを再度追加しています
クラウド サービス プロジェクトからロールを削除する場合は、後で、ロールをプロジェクトに追加することは、ロールの宣言とエンドポイントと診断の情報などの基本属性のみが追加されます。 その他のリソースや参照は追加されません、`ServiceDefinition.csdef`ファイルまたは、`ServiceConfiguration.cscfg`ファイル。 この情報を追加する場合は、手動でこれらのファイルに再度追加する必要があります。

たとえば、web サービスの役割を削除する場合があり、後で再びソリューションにこのロールを追加すること。 これを行うと、エラーが発生します。 このエラーを回避するには、追加する必要が、`<LocalResources>`要素には、次の XML に示すように、`ServiceDefinition.csdef`ファイル。 名前属性の一部としてプロジェクトに追加した web サービスの役割の名前を使用して、 **<LocalStorage>** 要素。 この例では、web サービス ロールの名前は**WCFServiceWebRole1**します。

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>次の手順
- [Visual Studio での Azure クラウド サービスのロールを構成します。](vs-azure-tools-configure-roles-for-cloud-service.md)
