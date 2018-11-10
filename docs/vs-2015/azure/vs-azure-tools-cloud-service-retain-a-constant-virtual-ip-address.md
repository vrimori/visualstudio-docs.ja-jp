---
title: Azure クラウド サービス用の固定仮想 IP アドレスを保持する方法 |Microsoft Docs
description: Azure クラウド サービスの仮想 IP アドレス (VIP) が変更されないようにする方法について説明します。
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002899"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Azure クラウド サービスの固定仮想 IP アドレスを保持する方法
Azure でホストされているクラウド サービスを更新するときに、サービスの仮想 IP アドレス (VIP) が変更されないようにする必要があります。 ドメイン管理サービスの多くは、ドメイン名を登録するためのドメイン ネーム システム (DNS) を使用します。 DNS は、VIP が同じ場合にのみ機能します。 使用することができます、**発行ウィザード**クラウド サービスの VIP が変更されないときにようにする Azure Tools で更新します。 クラウド サービスの DNS ドメインの管理を使用する方法の詳細については、次を参照してください。 [Azure クラウド サービスのカスタム ドメイン名を構成する](/azure/cloud-services/cloud-services-custom-domain-name-portal)します。

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>VIP を変更せずにクラウド サービスを発行します。
ときに、まず、Azure にデプロイする運用環境など、特定の環境では、クラウド サービスの VIP が割り当てられます。 VIP は、デプロイを明示的に削除するか、展開は、デプロイの更新プロセスによって暗黙的に削除している場合にのみ変更します。 VIP を保持する、デプロイを削除する必要がありますしないと、Visual Studio が、デプロイを自動的に削除されないことを確認する必要があります。 

展開設定を指定することができます、**発行ウィザード**、いくつかの展開オプションをサポートしています。 デプロイとして新規と、増分または同時更新プログラムの展開を指定することができます。 両方の種類の更新プログラムの展開では、VIP を保持します。 これらのさまざまな種類の展開の定義は、次を参照してください。 [Azure アプリケーション発行ウィザード](vs-azure-tools-publish-azure-application-wizard.md)します。 さらに、エラーが発生した場合、クラウド サービスの以前のデプロイが削除されたかどうかを制御できます。 そのオプションを正しく設定しない場合、VIP が予期せず変更可能性があります。

## <a name="update-a-cloud-service-without-changing-its-vip"></a>VIP を変更することがなくクラウド サービスを更新します。
1. 作成または Visual Studio で Azure クラウド サービス プロジェクトを開きます。 

2. **ソリューション エクスプ ローラー**プロジェクトを右クリックします。 ショートカット メニューでは、次のように選択します。**発行**します。

    ![発行メニュー](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. **Azure アプリケーションの発行** ダイアログ ボックスで、展開する Azure サブスクリプションを選択します。 選択し、必要に応じてサインイン**次**します。

    ![Azure アプリケーションのサインイン ページを発行します。](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. **一般的な設定** タブで、確認をデプロイするサービス、クラウドの名前を**環境**、**ビルド構成**と、 **サービス構成**がすべて正しい。

    ![Azure アプリケーションの共通設定 タブを発行します。](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. **詳細設定** タブで、いることを確認、**デプロイ ラベル**と**ストレージ アカウント**が正しい。 いることを確認、**配置エラーを削除** チェック ボックスがオフになって、いることを確認、**配置の更新** チェック ボックスをオンします。 オフにすると、**配置エラーを削除**デプロイ中にエラーが発生した場合、VIP が失われないことを確認するチェック ボックスをオンします。 選択して、**配置の更新**デプロイが削除され、アプリケーションを再発行するときに、VIP が失われないことを確認するチェック ボックスをオンします。 

    ![Azure アプリケーションの詳細設定 タブを発行します。](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. さらに、ロールの更新する方法を指定するには、選択**設定**横に**配置の更新**します。 いずれかを選択**増分更新**または**同時更新**、選択と**OK**します。 選択**増分更新**アプリケーションが常に使用できるように、アプリケーションの各インスタンスを 1 つずつ更新します。 選択**同時更新**を同時に、アプリケーションのすべてのインスタンスを更新します。 同時更新時間は短くなりますが、サービスが更新プロセス中には利用できません。 完了したら、選択**次**します。

    ![Azure アプリケーションの展開設定 ページを発行します。](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. **Azure アプリケーションの発行**ダイアログ ボックスで、**次**まで、**概要**ページが表示されます。 設定を確認し、**発行**します。
   
    ![Azure アプリケーションの概要 ページを発行します。](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>次の手順
- [Visual Studio を使用して Azure アプリケーション発行ウィザード](vs-azure-tools-publish-azure-application-wizard.md)

