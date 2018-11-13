---
title: Visual Studio での Azure クラウド サービス プロジェクトの構成 |Microsoft Docs
description: Visual Studio で、そのプロジェクトの要件に応じて、Azure クラウド サービス プロジェクトを構成する方法について説明します。
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 7417bc117de7dc472f413dd9145944cad2d48bb4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002952"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio で Azure クラウド サービス プロジェクトを構成する
そのプロジェクトの要件に応じて、Azure クラウド サービス プロジェクトを構成できます。 次のカテゴリのプロジェクトのプロパティを設定できます。

- **Azure クラウド サービスを発行**-既存のクラウド サービスを Azure にデプロイが誤って削除されないことを確認するプロパティを設定することができます。
- **ローカル コンピューター上のクラウド サービス実行またはデバッグ**-を使用して、Azure ストレージ エミュレーターを起動するかどうかを示すサービス構成を選択することができます。
- **作成時にそのクラウド サービス パッケージの検証**-を問題なく、クラウド サービス パッケージを展開することを確認できるように、すべての警告をエラーとして扱うことができます。 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Azure クラウド サービス プロジェクトを構成する手順
1. 開くか、Visual Studio でのクラウド サービス プロジェクトを作成します。

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、コンテキスト メニューから選択、**プロパティ**します。
   
1. プロジェクトのプロパティ ページで、選択、**開発**タブ。

    ![プロジェクトのプロパティ メニュー](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. 設定**既存のデプロイを削除する前にプロンプト**に**True**します。 この設定は、Azure で既存のデプロイが誤って削除されないことを確認するのに役立ちます

1. 目的の**サービス構成**をサービス構成を示すために実行またはクラウド サービスをローカルでデバッグするときに使用します。 ロールのサービス構成を変更する方法の詳細については、次を参照してください。 [Visual Studio で Azure クラウド サービスのロールを構成する方法](./vs-azure-tools-configure-roles-for-cloud-service.md)します。

1. 設定**Azure ストレージ エミュレーターの起動**に**True**実行またはクラウド サービスをローカルでデバッグするときに、Azure ストレージ エミュレーターを開始します。

1. 設定**警告をエラーとして扱う**に**True**パッケージ検証エラーがある場合に発行することはできないかどうかを確認します。

1. 設定**web プロジェクト ポートの使用**に**True** web ロールに同じポートが使用されるかどうかを確認するたびに IIS Express でローカルに開始します。

1. Visual Studio ツールバーで、次のように選択します。**保存**します。

## <a name="next-steps"></a>次の手順
- [複数のサービス構成を使用して Azure プロジェクトを構成します。](vs-azure-tools-multiple-services-project-configurations.md)

