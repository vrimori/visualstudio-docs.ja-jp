---
title: 接続済みサービスを使用して Azure Storage を追加する | Microsoft Docs
description: Visual Studio の [接続済みサービスの追加] ダイアログ ボックスを使用してアプリに Azure Storage を追加する
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev15
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: deb3a7cce793a1f10518ddc88b9ed6c22c55a090
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140579"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio 接続済みサービスを使用した Azure ストレージの追加

Visual Studio では、**[接続済みサービスの追加]** ダイアログを使用して、次のサービスを Azure Storage に接続できます。

- C# クラウド サービス
- .NET バックエンド モバイル サービス
- ASP.NET Web サイトまたはサービス
- ASP.NET Core サービス
- Azure WebJob サービス

接続済みサービス機能により、必要なすべての参照と接続コードがプロジェクトに追加され、構成ファイルが適切に変更されます。

完了後、**[接続済みサービスの追加]** ダイアログに、Blob Storage、キュー、およびテーブルの操作を開始するために必要な手順の詳細を示すドキュメントが自動的に表示されます。

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、[Visual Studio for Mac での接続済みサービス](/visualstudio/mac/connected-services)に関するページを参照してください。

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>[接続済みサービス] ダイアログを使用して Azure Storage に接続する

1. Visual Studio でプロジェクトを開きます。

1. **ソリューション エクスプローラー**で **[接続済みサービス]** ノードを右クリックし、コンテキスト メニューの **[接続済みサービスの追加]** を選択します。

    ![Azure の接続済みサービスを追加する](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. **[接続済みサービス]** ページで、**[Azure Storage を使用したクラウド ストレージ]** を選択します。

    ![Azure Storage を追加する](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **[Azure Storage]** ダイアログで、既存のストレージ アカウントを選択し、**[追加]** をクリックします。

    ストレージ アカウントを作成する必要がある場合は、次の手順に進みます。 必要ない場合は、手順 6 に進みます。

    ![既存のストレージ アカウントをプロジェクトに追加する](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. ストレージ アカウントを作成するには、以下の手順を実行します。

   1. ダイアログの下部にある **[新しいストレージ アカウントを作成します]** を選択します。

   1. **[ストレージ アカウントの作成]** ダイアログに入力し、**[作成]** をクリックします。

       ![新しい Azure ストレージ アカウント](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. **[Azure Storage]** ダイアログが表示されると、新しいストレージ アカウントが一覧に表示されます。 一覧で新しいストレージ アカウントを選択し、**[追加]** をクリックします。

1. プロジェクトの **[サービス参照]** ノードに、ストレージの接続済みサービスが表示されます。

## <a name="how-your-project-is-modified"></a>プロジェクトを変更する方法

ダイアログが完了すると、Visual Studio は参照を追加し、特定の構成ファイルを変更します。 具体的な変更内容はプロジェクトの種類によって異なります。

- ASP.NET プロジェクト - [変更内容 – ASP.NET プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core プロジェクト - [変更内容 – ASP.NET 5 プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513124)
- クラウド サービス プロジェクト (Web ロールおよび worker ロール) - [変更内容 – クラウド サービス プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- WebJob プロジェクト - [変更内容 - WebJob プロジェクト](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="see-also"></a>関連項目

- [MSDN フォーラム: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Microsoft Azure Storage チーム ブログ](http://blogs.msdn.com/b/windowsazurestorage/)
- [Azure Storage のドキュメント](https://docs.microsoft.com/azure/storage/)
- [接続済みサービス (Visual Studio for Mac)](/visualstudio/mac/connected-services)
