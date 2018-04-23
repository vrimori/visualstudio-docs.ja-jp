---
title: ClickOnce アプリケーションのテストの配置と再署名なしの実稼働サーバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4c71e1bd6f224fdd0198ce7850c92364126d7e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>再署名を行わない ClickOnce アプリケーションの配置 (テスト サーバーおよび運用サーバー)
このトピックでは、clickonce マニフェストにバージョン 3.5 を再署名したり、ClickOnce を変更せずに複数のネットワークの場所からの ClickOnce アプリケーションの展開を有効にする、.NET Framework で導入された新機能について説明します。  
  
> [!NOTE]
>  再署名は、新しいバージョンのアプリケーションの展開に適した方法ではまだです。 可能な限り、再署名を行うメソッドを使用します。 詳しくは、「[Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)」をご覧ください。  
  
 サード パーティの開発者や Isv オプトインできます、この機能にアプリケーションの更新に顧客に容易にします。 この機能は、次の状況で使用できます。  
  
-   更新する場合、アプリケーションでは、アプリケーションの最初のインストールではありません。  
  
-   コンピューター上のアプリケーションの構成が 1 つがある場合。 たとえば、2 つの異なるデータベースを指すようにアプリケーションを構成する場合は、この機能を使用することはできません。  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>配置マニフェストから deploymentProvider の除外  
 .NET Framework 2.0 と .NET Framework 3.0 でオフライン利用をシステムにインストールされる ClickOnce アプリケーションを指定する必要があります、`deploymentProvider`その配置マニフェストにします。 `deploymentProvider`は多くの場合、更新プログラムの場所と呼びます ClickOnce アプリケーションの更新プログラムをチェックする場所です。 この要件は、配置に署名するアプリケーションの発行者の必要性と組み合わせるを使用仕入先、またはその他のサード パーティからの ClickOnce アプリケーションを更新する会社の困難になることができます。 同じネットワーク上の複数の場所から同じアプリケーションの展開を困難になります。  
  
 .NET Framework 3.5 では、ClickOnce に加えられた変更には、その後、独自のネットワーク上のアプリケーションを展開できますが、別の組織に ClickOnce アプリケーションを提供するサード パーティ可能性があります。  
  
 この機能を利用するために、ClickOnce アプリケーションの開発者を除外する必要がある`deploymentProvider`マニフェストを展開します。 つまり、除外、 `-providerUrl` Mage.exe またはようにでマニフェストに引数の展開を作成するときに、**起動の場所**上のテキスト ボックス、**アプリケーション マニフェスト** タブは空白のまま場合します。MageUI.exe で配置マニフェストを生成しています。  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider とアプリケーションの更新  
 以降、.NET Framework 3.5 では、不要になった指定する必要が、`deploymentProvider`オンラインとオフラインの両方の使用状況の ClickOnce アプリケーションを展開するために、配置マニフェストにします。 これは、パッケージと、自分で配置に署名だけ、ネットワーク経由でアプリケーションを展開するには、他の企業を許可する必要があるシナリオをサポートします。  
  
 重要な点を除外するアプリケーション、`deploymentProvider`を含む更新プログラムを出荷するまで、更新する際、そのインストール場所を変更できません、`deploymentProvider`タグをもう一度です。  
  
 この点を明確にするための 2 つの例のとおりです。 最初の例を持たない ClickOnce アプリケーションを発行`deploymentProvider`からインストールしてタグ、してもらいますhttp://www.adatum.com/MyApplication/です。 場合に、アプリケーションからの次の更新を発行するhttp://subdomain.adatum.com/MyApplication/、することができなくなります内にある配置マニフェストにこのことを示すのhttp://www.adatum.com/MyApplication/します。 次の 2 つのいずれかの操作を行うことができます。  
  
-   以前のバージョンをアンインストールするユーザーに連絡し、新しい場所から、新しいバージョンをインストールします。  
  
-   更新プログラムを含めるhttp://www.adatum.com/MyApplication/が含まれている、`deploymentProvider`指すhttp://www.adatum.com/MyApplication/です。 次と後で別の更新プログラムをリリース`deploymentProvider`指すhttp://subdomain.adatum.com/MyApplication/です。  
  
 指定する ClickOnce アプリケーションを公開する 2 番目の例では、 `deploymentProvider`、それを削除しようとするとします。 1 回、新しいバージョンは`deploymentProvider`はダウンロードされてクライアントにすることはできませんが、アプリケーションのバージョンが解放されるまでの更新に使用するパスにリダイレクト`deploymentProvider`復元します。 最初の例と同様`deploymentProvider`更新の現在の場所、新しい場所ではなく最初に指す必要があります。 挿入しようとする場合、この場合、`deploymentProvider`を参照するhttp://subdomain.adatum.com/MyApplication/、次回の更新は失敗します。  
  
## <a name="creating-a-deployment"></a>展開を作成します。  
 別のネットワークの場所から展開可能な展開を作成する手順のガイダンスについては、次を参照してください[チュートリアル: ClickOnce アプリケーションをはありません必要な設定を指定の手動展開とその保持のブランド化情報](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)。  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)