---
title: ClickOnce アプリケーションのテストの配置と再署名なしの実稼働サーバー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2b2a26e847a23e8a4037958532889626a931341c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840039"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>再署名を行わない ClickOnce アプリケーションの配置 (テスト サーバーおよび運用サーバー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックでは、clickonce マニフェストをバージョン 3.5 再署名または ClickOnce を変更せずに複数のネットワークの場所からの ClickOnce アプリケーションの展開をできるようにする .NET Framework で導入された新機能について説明します。  
  
> [!NOTE]
>  署名は、新しいバージョンのアプリケーションをデプロイするための推奨される方法ではまだです。 可能であれば、再署名を行うメソッドを使用します。 詳しくは、「[Mage.exe (マニフェストの生成および編集ツール)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)」をご覧ください。  
  
 サード パーティ製の開発者や Isv オプトインできる、この機能にアプリケーションを更新する顧客に容易にします。 この機能は、次の状況で使用できます。  
  
-   ときに、アプリケーション、アプリケーションの最初のインストールではなくを更新しています。  
  
-   コンピューター上のアプリケーションの 1 つだけの構成がある場合。 たとえば、2 つの異なるデータベースをポイントするアプリケーションを構成すると、この機能を使用することはできません。  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>配置マニフェストからの deploymentProvider の除外  
 .NET Framework 2.0 と .NET Framework 3.0 でオフライン利用のシステムにインストールされる ClickOnce アプリケーションを指定する必要があります、`deploymentProvider`配置マニフェストにします。 `deploymentProvider`更新プログラムの場所とも呼ば ClickOnce がアプリケーションの更新をチェックする場所です。 配置に署名するアプリケーションの発行者の必要性と組み合わせると、この要件を使用企業がベンダーやその他のサード パーティからの ClickOnce アプリケーションを更新する困難になることができます。 同じネットワーク上の複数の場所から同じアプリケーション デプロイにくくします。  
  
 .NET Framework 3.5 では、ClickOnce に加えられた変更は、その後、独自のネットワーク上のアプリケーションを展開できますが、別の組織に ClickOnce アプリケーションを提供するサード パーティ可能性があります。  
  
 この機能を利用するには、ClickOnce アプリケーションの開発者を除外する必要があります`deploymentProvider`マニフェストを展開します。 つまり、除外、`-providerUrl`されるようにしたり、Mage.exe でマニフェストの展開を作成するときに、引数、**起動の場所**上のテキスト ボックス、**アプリケーション マニフェスト** タブは空白のまま場合します。MageUI.exe で配置マニフェストを生成します。  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider とアプリケーションの更新プログラム  
 以降、.NET Framework 3.5 では、不要になった指定する必要が、`deploymentProvider`オンラインとオフラインの両方の使用状況の ClickOnce アプリケーションをデプロイするには、配置マニフェスト。 これをパッケージ化と配置に署名する、自分でにより、他の企業は自社のネットワーク経由でアプリケーションをデプロイする必要があるシナリオをサポートしています。  
  
 重要なポイントは除外するアプリケーション、`deploymentProvider`出荷されるは、更新プログラムが含まれるまで、更新する際のインストール場所を変更ことはできません、`deploymentProvider`タグをもう一度。  
  
 この点を明確にする 2 つの例を示します。 ない ClickOnce アプリケーションを発行する最初の例では、`deploymentProvider`してからインストールして、タグもらいます http://www.adatum.com/MyApplication/ します。 アプリケーションからの次の更新を発行したい場合 http://subdomain.adatum.com/MyApplication/、配置マニフェスト内にあることを示すこの方法はありません http://www.adatum.com/MyApplication/します。 次の 2 つのいずれかの操作を行うことができます。  
  
- 以前のバージョンをアンインストールするユーザーに通知し、新しい場所から新しいバージョンをインストールします。  
  
- 更新プログラムを含める http://www.adatum.com/MyApplication/ を含む、`deploymentProvider`を指す http://www.adatum.com/MyApplication/ します。 次に、後で別の更新プログラムをリリース`deploymentProvider`を指す http://subdomain.adatum.com/MyApplication/ します。  
  
  2 番目の例を指定する ClickOnce アプリケーションを発行する`deploymentProvider`、削除対象とするとします。 なしの新しいバージョンに 1 回`deploymentProvider`がダウンロードされて、クライアントにすることができなくを持つアプリケーションのバージョンをリリースするまで更新に使用されるパスにリダイレクトする`deploymentProvider`復元します。 最初の例と同じ`deploymentProvider`更新の現在の場所、新しい場所ではなく最初に指す必要があります。 挿入しようとした場合、この場合、`deploymentProvider`を参照する http://subdomain.adatum.com/MyApplication/、次回の更新は失敗します。  
  
## <a name="creating-a-deployment"></a>展開の作成  
 別のネットワークの場所から展開可能な展開を作成する手順のガイダンスについては、次を参照してください[チュートリアル: ClickOnce アプリケーションをはありません必要な設定を指定の手動展開とその保持のブランド化情報](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)。  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)



