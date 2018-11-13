---
title: Visual Studio 接続済みサービスを使用して Azure Storage の追加 |Microsoft Docs
description: Visual Studio 接続されているサービスの追加 ダイアログ ボックスを使用して、アプリを Azure Storage を追加します。
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002339"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio 接続済みサービスを使用して Azure storage の追加
Visual Studio を使用して接続できます、次のいずれかを Azure Storage を使用して、**接続済みサービスの追加**ダイアログ。

- C#クラウド サービス
- .NET バックエンド モバイル サービス
- ASP.NET web サイトまたはサービス
- ASP.NET Core サービス
- Azure WebJob サービス 

接続済みサービス機能をプロジェクトにすべての必要な参照と接続コードを追加し、構成ファイルを適切に変更します。 

完了した後、**接続済みサービスの追加**ダイアログは自動的にキュー、blob storage との作業を開始するための手順を詳しく説明するドキュメントを表示し、テーブルします。

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>接続済みサービス ダイアログを使用して Azure Storage への接続します。
1. Visual Studio でプロジェクトを開きます

1. **ソリューション エクスプ ローラー**を右クリックし、**接続済みサービス**ノード、および選択し、コンテキスト メニューから**接続済みサービス**します。
   
    ![Azure の追加の接続済みサービス](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. **接続済みサービス**] ページで、[ **Azure Storage を使用したクラウド ストレージ**します。
   
    ![Azure Storage を追加します。](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **Azure Storage**ダイアログで、既存のストレージ アカウントを選択し選択**追加**します。
   
    ストレージ アカウントを作成する必要がある場合は、次の手順に移動します。 それ以外の場合、手順 6. に進みます。
    
    ![プロジェクトに既存のストレージ アカウントを追加します。](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. ストレージ アカウントを作成します。 
   
   1. 選択**新しいストレージ アカウント作成**ダイアログの下部にあります。

   1. 記入、**ストレージ アカウントの作成**ダイアログ、および選択**作成**です。
      
       ![新しい Azure ストレージ アカウント](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. ときに、 **Azure Storage**ダイアログが表示されたら、新しいストレージ アカウントが一覧に表示されます。 一覧で、新しいストレージ アカウントを選択し、選択**追加**します。

1. 接続済みサービスのもと、ストレージ、**サービス参照**プロジェクトのノード。
   
## <a name="how-your-project-is-modified"></a>プロジェクトを変更する方法
ダイアログが終了したら、Visual Studio は参照を追加し、特定の構成ファイルを変更します。 特定の変更は、プロジェクトの種類によって異なります。 

- ASP.NET プロジェクト -[内容 – ASP.NET プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core プロジェクト -[内容 – ASP.NET 5 プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- クラウド サービス プロジェクト (web ロールと worker ロール) -[内容 – クラウド サービス プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- WebJob プロジェクト -[内容 - WebJob プロジェクト](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>次の手順
- [Azure Storage の MSDN フォーラム:](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Microsoft Azure Storage チーム ブログ](http://blogs.msdn.com/b/windowsazurestorage/)
- [Azure Storage のドキュメント](https://docs.microsoft.com/azure/storage/)
