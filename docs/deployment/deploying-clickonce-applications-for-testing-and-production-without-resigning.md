---
title: ClickOnce アプリケーションのテストの配置と再署名なしの実稼働サーバー |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5214eef80f7417bb319fc0157c233901a12ee86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994395"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>署名なしの ClickOnce アプリケーションのテストと実稼働サーバーの展開します。
この記事では、マニフェストをバージョン 3.5 再署名または ClickOnce を変更せずに複数のネットワークの場所からの ClickOnce アプリケーションの展開をできるようにする .NET Framework で導入された ClickOnce の機能について説明します。  
  
> [!NOTE]
>  署名は、新しいバージョンのアプリケーションをデプロイするための推奨される方法ではまだです。 可能であれば、再署名を行うメソッドを使用します。 詳細については、「[*Mage.exe* (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)」をご覧ください。  
  
 サード パーティ製の開発者や Isv オプトインできますこの機能により、アプリケーションを更新する顧客に容易にします。 この機能は、次の状況で使用できます。  
  
-   ときに、アプリケーションの最初のインストールではなく、アプリケーションを更新しています。  
  
-   コンピューター上のアプリケーションの 1 つだけの構成がある場合。 たとえば、2 つの異なるデータベースをポイントするアプリケーションを構成すると、この機能を使用することはできません。  
  
## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>配置マニフェストの deploymentProvider を除外します。  
 .NET Framework 2.0 と .NET Framework 3.0 でオフライン利用のシステムにインストールされる ClickOnce アプリケーションを一覧表示する必要があります、`deploymentProvider`配置マニフェストにします。 `deploymentProvider`更新プログラムの場所とも呼ば ClickOnce がアプリケーションの更新プログラムをチェックする場所です。 配置に署名するアプリケーションの発行者の必要性と、この要件を使用企業がベンダーやその他のサード パーティからの ClickOnce アプリケーションを更新する困難になることができます。 同じネットワーク上の複数の場所から同じアプリケーション デプロイにくくします。  
  
 .NET Framework 3.5 では、ClickOnce に加えられた変更は、その後、独自のネットワーク上のアプリケーションを展開できますが、別の組織に ClickOnce アプリケーションを提供するサード パーティ製可能性があります。  
  
 この機能を利用するには、ClickOnce アプリケーションの開発者を除外する必要があります`deploymentProvider`マニフェストを展開します。 この要件では、除外する必要がある、`-providerUrl`引数展開を作成するときに、Mage.exe を使用してマニフェストします。 または、MageUI.exe で配置マニフェストを生成している場合をする必要があることを確認します、**起動場所**上のテキスト ボックス、**アプリケーション マニフェスト** タブは空白のままにします。  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider とアプリケーションの更新プログラム  
 以降、.NET Framework 3.5 では、不要になった指定する必要が、`deploymentProvider`オンラインとオフラインの両方の使用状況の ClickOnce アプリケーションをデプロイするには、配置マニフェスト。 この変更をパッケージ化と配置に署名する、自分でにより、他の企業は自社のネットワーク経由でアプリケーションをデプロイする必要があるシナリオをサポートしています。  
  
 重要な点を除外するアプリケーション、`deploymentProvider`出荷されるは、更新プログラムが含まれるまで、更新する際のインストール場所を変更ことはできません、`deploymentProvider`タグをもう一度。  
  
 この点を明確にする 2 つの例を示します。 ない ClickOnce アプリケーションを発行する最初の例では、`deploymentProvider`してからインストールして、タグもらいます http://www.adatum.com/MyApplication/します。 アプリケーションからの次の更新を発行したい場合 http://subdomain.adatum.com/MyApplication/、配置マニフェスト内にあるでこれを表す方法があるない http://www.adatum.com/MyApplication/します。 次の 2 つのいずれかの操作を行うことができます。  
  
- 以前のバージョンをアンインストールするユーザーに通知し、新しい場所から新しいバージョンをインストールします。  
  
- 更新プログラムを含める http://www.adatum.com/MyApplication/を含む、`deploymentProvider`を指す http://www.adatum.com/MyApplication/します。 次に、後で別の更新プログラムをリリース`deploymentProvider`を指す http://subdomain.adatum.com/MyApplication/します。  
  
  2 番目の例を指定する ClickOnce アプリケーションを発行する`deploymentProvider`、削除対象とするとします。 なしの新しいバージョンに 1 回`deploymentProvider`ダウンロードをクライアントに更新プログラムを持つアプリケーションのバージョンをリリースするまでに使用されるパスにリダイレクトすることはできません`deploymentProvider`復元します。 最初の例と同じ`deploymentProvider`更新の現在の場所、新しい場所ではなく最初に指す必要があります。 挿入しようとした場合、この場合、`deploymentProvider`を参照する http://subdomain.adatum.com/MyApplication/、次回の更新は失敗します。  
  
## <a name="create-a-deployment"></a>配置の作成  
 別のネットワークの場所から展開できる展開の作成のステップ バイ ステップ ガイダンスについては、次を参照してください。[チュートリアル。再署名が要求されるされないブランド情報を保持する ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)します。  
  
## <a name="see-also"></a>関連項目  
 [*Mage.exe* (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [*MageUI.exe* (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)