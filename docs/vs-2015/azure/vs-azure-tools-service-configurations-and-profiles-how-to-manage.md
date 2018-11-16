---
title: サービス構成とプロファイルを管理する方法 |Microsoft Docs
description: サービスの構成とプロファイル構成ファイルで作業する方法について説明します |デプロイ環境の設定を格納し、クラウド サービスの設定を発行します。
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002919"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>サービス構成とプロファイルを管理する方法
## <a name="overview"></a>概要
Visual Studio が 2 つの種類の構成ファイルで構成情報を格納するクラウド サービスを発行する場合: サービス構成とプロファイル。 サービス構成 (.cscfg ファイル) には、Azure クラウド サービスのデプロイ環境の設定が保存されます。 Azure は、クラウド サービスを管理する場合に、これらの構成ファイルを使用します。 その一方で、プロファイル (.azurePubxml ファイル) のストアは、クラウド サービスの設定を発行します。 これらの設定は、発行ウィザードを使用して Visual Studio によってローカルで使用されるときの選択内容を記録します。 このトピックでは、両方の種類の構成ファイルを操作する方法について説明します。

## <a name="service-configurations"></a>サービスの構成
各デプロイ環境を使用する複数のサービス構成を作成することができます。 たとえば、実行し、Azure アプリケーションと、運用環境の別のサービス構成のテストに使用するローカル環境用のサービス構成を作成します。

追加できますが、削除、名前の変更、および要件に基づいて、これらのサービス構成を変更します。 次の図に示すように、Visual Studio からこれらのサービス構成を管理できます。

![サービス構成の管理](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

開くことも、**構成の管理**ロールのプロパティ ページから ダイアログ ボックス。 Azure プロジェクトのロールのプロパティを開くには、そのロールのショートカット メニューを開きし、**プロパティ**します。 **設定**] タブで、展開、**サービス構成**、一覧表示し、[**管理**を開く、**構成の管理**ダイアログ ボックス。

### <a name="to-add-a-service-configuration"></a>サービス構成を追加するには
1. ソリューション エクスプ ローラーで、Azure プロジェクトのショートカット メニューを開き、クリックして**構成の管理**します。
   
    **サービス構成の管理** ダイアログ ボックスが表示されます。
2. サービス構成を追加するには、既存の構成のコピーを作成する必要があります。 これを行うには、名前の一覧からコピーし、選択する構成を選択**コピー作成**です。
3. (省略可能)サービス構成に別の名前を付けて、名の一覧から新しいサービス構成を選択し、**の名前を変更**します。 **名前**テキスト ボックスに、このサービス構成を使用し、選択する名前を入力**OK**します。
   
    ServiceConfiguration という新しいサービス構成ファイル。[New Name] .cscfg は、ソリューション エクスプ ローラーで Azure プロジェクトに追加されます。

### <a name="to-delete-a-service-configuration"></a>サービス構成を削除するには
1. ソリューション エクスプ ローラーで、Azure プロジェクトのショートカット メニューを開き、クリックして**構成の管理**します。
   
    **サービス構成の管理** ダイアログ ボックスが表示されます。
2. サービス構成を削除する選択から削除する構成、**名前**を一覧表示し、**削除**します。 この構成を削除することを確認するダイアログ ボックスが表示されます。
3. 選択**削除**します。
   
     サービス構成ファイルは、ソリューション エクスプ ローラーで Azure プロジェクトから削除されます。

### <a name="to-rename-a-service-configuration"></a>サービス構成の名前を変更するには
1. ソリューション エクスプ ローラーで、Azure のプロジェクトのショートカット メニューを開き、クリックして**構成の管理**します。
   
    **サービス構成の管理** ダイアログ ボックスが表示されます。
2. サービス構成の名前を変更するから新しいサービス構成を選択して、**名前**、一覧表示し、**の名前を変更**します。 **名前**テキスト ボックスに、このサービス構成を使用し、選択する名前を入力**OK**します。
   
    ソリューション エクスプ ローラーで Azure プロジェクトでは、サービス構成ファイルの名前が変更されます。

### <a name="to-change-a-service-configuration"></a>サービス構成を変更するには
* サービス構成を変更する場合は、Azure のプロジェクトに変更し、選択する特定のロールのショートカット メニューを開き**プロパティ**します。 参照してください[方法: Visual Studio で Azure クラウド サービスの役割を構成する](vs-azure-tools-configure-roles-for-cloud-service.md)詳細についてはします。

## <a name="make-different-setting-combinations-by-using-profiles"></a>プロファイルを使用して別の設定の組み合わせを作成します。
プロファイルを使用すると、自動的に記入すること、**発行ウィザード**さまざまな目的の設定の組み合わせが異なります。 たとえば、デバッグ用の 1 つのプロファイルがあることができ、リリース用に別のビルドします。 その場合は、**デバッグ**プロファイルが必要があります**IntelliTrace**有効になっていると、**デバッグ**選択すると、構成、および**リリース**プロファイルが必要があります**IntelliTrace**無効になっていると、**リリース**構成が選択します。 別のストレージ アカウントを使用してサービスをデプロイするのにさまざまなプロファイルを使用することもできます。

最初に、ウィザードを実行する場合は、既定のプロファイルが作成されます。 Visual Studio は、下の Azure プロジェクトに追加される .azurePubXml 拡張子を持つファイルにプロファイルを格納、**プロファイル**フォルダー。 手動で、後で、ウィザードを実行するときは、さまざまな選択を指定、ファイルが自動的に更新します。 次の手順を実行する前にする必要がありますが既にパブリッシュは、クラウド サービスを少なくとも 1 回。

### <a name="to-add-a-profile"></a>プロファイルを追加するには
1. Azure プロジェクトのショートカット メニューを開きを選択します**発行**します。
2. 横に、**ターゲット プロファイル**一覧で、、**プロファイルの保存**として次の図は、ボタンをクリックします。 プロファイルが作成されます。
   
    ![新しいプロファイルを作成します。](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. プロファイルが作成された後、選択 **< 管理… >** で、**ターゲット プロファイル**一覧。
   
    **プロファイルの管理**として次の図は、ダイアログ ボックスが表示されます。
   
    ![管理プロファイル ダイアログ ボックス](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. **名前**ボックスの一覧で、プロファイルを選択し、**コピーの作成**です。
5. 選択、**閉じる**ボタンをクリックします。
   
    新しいプロファイルは、[ターゲット プロファイル] 一覧が表示されます。
6. **ターゲット プロファイル**一覧で、先ほど作成したプロファイルを選択します。 選択したプロファイルから、発行ウィザードの設定が入力されます。
7. 選択、**前**と**次**、発行ウィザードの各ページを表示し、このプロファイルの設定をカスタマイズするボタン。 参照してください[Azure アプリケーション発行ウィザード](http://go.microsoft.com/fwlink/p/?LinkID=623085)について。
8. 設定のカスタマイズが完了したら、選択**次**設定 ページに戻ります。 これらの設定を使用して、サービスを発行するとき、または選択した場合、プロファイルを保存**保存**プロファイルの一覧の横にあります。

### <a name="to-rename-or-delete-a-profile"></a>名前を変更したり、プロファイルを削除するには
1. Azure プロジェクトのショートカット メニューを開きを選択します**発行**します。
2. **ターゲット プロファイル**一覧で、**管理**します。
3. **プロファイルの管理**ダイアログ ボックスで選択プロファイルを削除して、選択**削除**します。
4. [確認] ダイアログ ボックスが表示されますが、選択**OK**します。
5. 選択**閉じる**します。

### <a name="to-change-a-profile"></a>プロファイルを変更するには
1. Azure プロジェクトのショートカット メニューを開きを選択します**発行**します。
2. **ターゲット プロファイル**一覧で、変更するプロファイルを選択します。
3. 選択、**前**と**次**、発行ウィザードの各ページを表示して目的の設定を変更するボタン。 参照してください[Azure アプリケーション発行ウィザード](http://go.microsoft.com/fwlink/p/?LinkID=623085)について。
4. 設定の変更が完了したら、選択**次**に戻る、**設定**ページ。
5. (省略可能)**発行**新しい設定を使用してクラウド サービスを発行します。 この時点でクラウド サービスを発行したくない、発行ウィザードを閉じると、Visual Studio が表示されたら、プロファイルに変更を保存するかどうか。

## <a name="next-steps"></a>次の手順
Visual Studio から Azure プロジェクトの他の部分を構成する方法については、次を参照してください[Azure プロジェクトの構成。](http://go.microsoft.com/fwlink/p/?LinkID=623075)
