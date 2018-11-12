---
title: Visual Studio を使用した Azure クラウド サービス プロジェクトの作成 |Microsoft Docs
description: Visual Studio で Azure クラウド サービス プロジェクトを作成するについて説明します
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003029"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio を使用した Azure クラウド サービス プロジェクトの作成
Azure Tools for Visual Studio プロジェクト テンプレートを作成することができますを提供する、 [Azure クラウド サービス](/azure/cloud-services/cloud-services-choose-me)、簡単な汎用の Azure サービスであります。 プロジェクトが作成されたら、Visual Studio では、構成、デバッグ、および Azure クラウド サービスをデプロイすることができます。

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Visual Studio で Azure クラウド サービス プロジェクトを作成する手順
このセクションでは、1 つまたは複数の web ロールと Visual Studio で Azure クラウド サービス プロジェクトを作成します。  

1. 管理者として Visual Studio を起動します。

1. メイン メニューで、次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

1. 選択**クラウド**ビジュアルからC#または Visual Basic プロジェクト テンプレート ノード、および選択**Azure クラウド サービス**テンプレートの一覧から。

    ![新しい Azure クラウド サービス](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. プロジェクトの開発を使用する .NET Framework のバージョンを指定します。

1. 名前と、プロジェクトの場所とソリューションの名前を入力します。 

1. **[OK]** を選択します。

1. **新しい Microsoft Azure クラウド サービス**ダイアログ ボックスで、追加するロールを選択し、ソリューションに追加する右矢印ボタンをクリックします。

    ![新しい Azure クラウド サービスの役割を選択します。](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. 追加したロールの名前を変更するロールでホバー、**新しい Microsoft Azure クラウド サービス**ダイアログ ボックスとし、コンテキスト メニューから、**の名前を変更**します。 ソリューション内でロールを変更することもできます (で、**ソリューション エクスプ ローラー**) が追加されています。

    ![Azure クラウド サービス ロールの名前を変更します。](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure プロジェクトでは、ソリューションでロール プロジェクトに関連付けが。 プロジェクトにも含まれています、*サービス定義ファイル*と*サービス構成ファイル*:

- **サービス定義ファイル**-、必要なロールを含め、アプリケーション、エンドポイント、および仮想マシンのサイズのランタイム設定を定義します。 
- **サービス構成ファイル**-ロールのインスタンスの数が実行され、ロールに対して定義されている設定の値を構成します。 

これらのファイルの詳細については、次を参照してください。 [Visual Studio での Azure クラウド サービス ロール構成](vs-azure-tools-configure-roles-for-cloud-service.md)します。

## <a name="next-steps"></a>次の手順
- [Visual Studio を使用した Azure クラウド サービス プロジェクトでのロールの管理](./vs-azure-tools-cloud-service-project-managing-roles.md)
