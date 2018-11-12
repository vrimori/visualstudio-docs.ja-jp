---
title: Cloud Explorer で Azure リソースの管理 |Microsoft Docs
description: Cloud Explorer を使用して参照し、Visual Studio 内での Azure リソースを管理する方法について説明します。
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002362"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Visual Studio Cloud Explorer で Azure アカウントに関連付けられているリソースを管理する

Cloud Explorer では、Azure リソースとリソース グループを表示、それらのプロパティを検査および Visual Studio 内から開発者が重要な診断操作を実行することができます。 

ように、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)、Cloud Explorer は、Azure Resource Manager スタック上に構築します。 そのため、クラウド エクスプ ローラーは、Azure リソース グループなどのリソースと Logic apps や API apps などの Azure サービスを理解し、サポート[ロール ベース access control](/azure/role-based-access-control/role-assignments-portal.md) (RBAC)。 

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2015 with、 [Microsoft Azure SDK for .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657)します。
* Microsoft Azure アカウントの場合は、アカウントを持っていない[無料試用版にサインアップ](http://go.microsoft.com/fwlink/?LinkId=623901)または[Visual Studio サブスクリプション会員の特典をアクティブ化](http://go.microsoft.com/fwlink/?LinkId=623901)します。

> [!NOTE]
> クラウド エクスプ ローラーを表示する選択**ビュー** > **Cloud Explorer**メニュー バーでします。

## <a name="add-an-azure-account-to-cloud-explorer"></a>追加の Azure アカウントをクラウド エクスプ ローラー

Azure アカウントに関連付けられているリソースを表示するには、は、まずクラウド エクスプ ローラーに、アカウントを追加する必要があります。 

1. **Cloud Explorer**、 **Azure アカウントの設定**します。

   ![クラウド エクスプ ローラーの Azure アカウントの設定 アイコン](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. 選択**アカウントを管理する**します。 

   ![クラウド エクスプ ローラーのアカウントの追加リンク](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. 参照する必要があるリソース Azure アカウントにログインします。 

1. Azure アカウントにログインするとそのアカウントに関連付けられているサブスクリプションを表示します。 参照して選択し、必要なアカウントのサブスクリプションのチェック ボックスをオン**適用**します。 

   ![Cloud Explorer: 表示する Azure サブスクリプションを選択します](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. 参照するリソースを含むサブスクリプションを選択すると、それらのサブスクリプションとリソースをクラウド エクスプ ローラーで表示します。

   ![クラウド エクスプ ローラーのリソースに対する Azure のアカウントを表示します。](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Cloud Explorer から Azure アカウントを削除します。 

1. **Cloud Explorer**、**アカウント管理**します。

   ![クラウド エクスプ ローラーの Azure アカウントの設定 アイコン](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. 削除するアカウントの横にある次のように選択します。 **Manage Accounts**します。

   ![クラウド エクスプ ローラーの Azure アカウントの設定 アイコン](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. 選択**削除**アカウントを削除します。

    ![クラウド エクスプ ローラーの管理アカウント ダイアログ ボックス](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>リソースの種類またはリソース グループを表示します。

Azure リソースを表示する、いずれかを選択できます**リソースの種類**または**リソース グループ**ビュー。

1. **Cloud Explorer**、リソース ビュー ドロップダウンを選択します。

   ![クラウド エクスプ ローラーのドロップダウン リストに目的のリソース ビューを選択します。](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. コンテキスト メニューから目的のビューを選択します。 

   * **リソースの種類**で使用される一般的なビューを表示、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)、web アプリ、ストレージ アカウント、および仮想マシンなどの種類によってカテゴリ化される Azure リソースに表示されます。 
   * **リソース グループ**- 関連付けられている Azure リソース グループによって分類の Azure リソースを表示します。 リソース グループは、特定のアプリケーションで使用される通常の Azure リソースのバンドルです。 Azure リソース グループの詳細については、次を参照してください。 [Azure Resource Manager の概要](/azure/azure-resource-manager/resource-group-overview)します。

   次の図は、2 つのリソース ビューの比較を示しています。

   ![クラウド エクスプ ローラーのリソース ビューの比較](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>表示し、クラウド エクスプ ローラーでリソースを移動します

Azure のリソースに移動し、クラウド エクスプ ローラーでその情報を表示、項目の種類または関連付けられているリソース グループを展開し、リソースを選択します。 リソースを選択する - 2 つのタブに情報が表示されます。**アクション**と**プロパティ**- クラウド エクスプ ローラーの下部にあります。

* **アクション** タブ - 選択したリソースに対して Cloud Explorer で実行できるアクションを一覧表示されます。 コンテキスト メニューを表示するリソースを右クリックして、これらのオプションを表示することもできます。

* **プロパティ**タブ - その種類、ロケール、およびリソース グループが関連付けられているなど、リソースのプロパティを示しています。

次の図は、表示される内容の各タブで、App Service の比較の例を示しています。

  ![Cloud Explorer のスクリーン ショット](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

すべてのリソースにアクション**ポータルで開く**します。 クラウド エクスプ ローラーで選択したリソースを表示このアクションを選択すると、 [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040)します。 **ポータルで開く**機能は、深く入れ子になったリソースに移動するのに便利です。

追加のアクションとプロパティの値が Azure のリソースに基づいても可能性があります表示。 たとえば、web apps と logic apps もあるアクション**ブラウザーで開く**と**デバッガーをアタッチ**に加えて**ポータルで開く**します。 エディターを開くアクションは、ストレージ アカウントの blob、キュー、またはテーブルを選択すると表示されます。 Azure アプリが**URL**と**状態**記憶域リソースがキーと接続文字列プロパティのプロパティ。

## <a name="find-resources-in-cloud-explorer"></a>Cloud Explorer でリソースを検索します。

Azure アカウントのサブスクリプションで特定の名前のリソースを検索するには、内の名前を入力します。、**検索**クラウド エクスプ ローラーでボックス。

  ![Cloud Explorer でのリソースの検索](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

内の文字を入力すると、**検索**がリソース ツリーにボックスで、その文字に一致するリソースのみが表示されます。
