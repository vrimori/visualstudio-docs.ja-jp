---
title: "ClickOnce アプリケーションを展開する他のユーザーの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d3a9762872f74b39d8cef387703488c01647dbcc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>開発者以外が配置する ClickOnce アプリケーションの作成
ClickOnce 配置を作成しているすべての開発者は、アプリケーション自体の展開を計画します。 それらの多くは、ClickOnce を使用してアプリケーションをパッケージし、し、ファイルを大規模な企業など、顧客に渡します。 お客様は、そのネットワーク上のアプリケーションをホストする役割の 1 つになります。 このトピックでは、.NET Framework バージョン 3.5 より前のバージョンでは、このような展開に固有の問題について説明します。 .NET Framework 3.5 では、新しい「信頼のマニフェストを使用して」機能を使用して、新しい解決し、について説明します。 最後に、.NET Framework の旧バージョンを使用して引き続きお客様の ClickOnce 配置を作成するための推奨される方針にで終わりです。  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>お客様の展開の作成に関連する問題  
 顧客に配置を提供する予定の場合、いくつかの問題が発生します。 最初の問題は、コード署名に関するものです。 ネットワーク経由で、展開するために、配置マニフェストとアプリケーション マニフェストの ClickOnce 配置する必要があります両方で署名するデジタル証明書。 これには、マニフェストに署名するときに、開発者の証明書または顧客の証明書を使用するかどうかの質問を発生させます。  
  
 配置マニフェストのデジタル署名で ClickOnce アプリケーションの id をベースとして使用する証明書の問題は重要、です。 開発者が、配置マニフェストに署名する場合は、顧客大企業では、社内の部署が 1 つ以上のアプリケーションのカスタマイズ バージョンを配置する場合の競合する可能性があります。  
  
 たとえば、Adventure Works の金融部門および人事部であること。 両方の部門、SQL データベースに格納されたデータからレポートを生成する Microsoft Corporation からの ClickOnce アプリケーションのライセンスを取得します。 Microsoft では、各部門に、それぞれのデータにカスタマイズされているアプリケーションのバージョンを提供します。 場合は、アプリケーションは、同じの Authenticode 証明書で署名が、両方のアプリケーションを使用しようとしたユーザーはエラーが発生、ClickOnce は、最初と同じものとして 2 番目のアプリケーションを見なすようにします。 ここでは、お客様は、予測不可能な望ましくない副作用を含む、アプリケーションでローカルに格納されているデータの損失を発生する可能性があります。  
  
 コードの署名は、関連するその他の問題、 `deploymentProvider` ClickOnce アプリケーションの更新プログラムを検索する場所が示されます配置マニフェスト内の要素。 この要素には署名の前に、配置マニフェストに追加します。 この要素は後で追加された、配置マニフェストが再署名する必要があります。  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>配置マニフェストの署名に顧客を必要とします。  
 開発者がアプリケーション マニフェスト、署名には、一意でない配置の問題の 1 つのソリューションと顧客配置マニフェストに署名します。 このアプローチは、他の懸案事項が導入されています。 Authenticode 証明書は、保護された資産を維持する必要があります、ため、顧客できませんだけ開発者に提供証明書配置に署名します。 顧客が配置マニフェストの署名自体、.NET Framework SDK を自由に使用できるツールを使用して、ときに、顧客がまたは処理を提供できるものよりも詳細な技術サポート技術が必要です。 開発者は、このような場合で、アプリケーション、Web サイト、または顧客が署名用のアプリケーションのバージョンを送信する他のメカニズムが通常作成します。  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>ClickOnce アプリケーションのセキュリティでのサインオンに顧客の影響  
 場合でも、開発者と顧客は、顧客がアプリケーション マニフェストに署名する必要がありますに同意すると、この信頼されたアプリケーション配置を適用する際に特にをアプリケーションの id を囲んでいるその他の問題を発生させます。 (この機能の詳細については、次を参照してください[信頼されたアプリケーションの展開の概要](../deployment/trusted-application-deployment-overview.md)。)。Adventure Works を by Microsoft Corporation に提供されているすべてのアプリケーションが完全信頼で実行されるように、クライアント コンピューターを構成する必要があることを言います。 Adventure Works は、配置マニフェストに署名をし、ClickOnce を使用して Adventure 作業のセキュリティ署名アプリケーションの信頼レベルを決定します。  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>信頼のアプリケーション マニフェストを使用してお客様の展開を作成します。  
 .NET Framework 3.5 では、ClickOnce にはマニフェストの署名方法のシナリオへの開発者および顧客、新しいソリューションを提供する、新しい機能が含まれています。 ClickOnce アプリケーション マニフェストは、という名前の新しい要素をサポートしている`<useManifestForTrust>`をアプリケーション マニフェストのデジタル署名は、信頼の決定に使用されることを示すために、開発者を有効にします。 開発者は ClickOnce パッケージ化ツールを使用: Mage.exe、MageUI.exe、および Visual Studio など-アプリケーション マニフェストにこの要素を含めると同様に、マニフェストには発行者名およびアプリケーションの名前の両方を埋め込みます。  
  
 使用する場合`<useManifestForTrust>`、配置マニフェストを証明機関によって発行された、Authenticode 証明書で署名する必要はありません。 代わりに、自己署名証明書と呼ばれるもので署名することができます。 自己署名証明書では、標準の .NET Framework SDK ツールを使用して、顧客または開発者によって生成され、標準の ClickOnce 配置ツールを使用して、配置マニフェストに適用されます。 詳細については、次を参照してください。 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)です。  
  
 配置マニフェストの自己署名証明書を使用して、いくつかの利点について説明します。 取得または独自の Authenticode 証明書を作成する必要がある、`<useManifestForTrust>`開発者は、アプリケーションでは独自のブランド id を管理しながら、顧客の展開を簡略化します。 セキュリティを強化され、一意のアプリケーション id を持っているされる符号付きの配置のセットになります。 これにより、複数の顧客に同じアプリケーションを配置から発生する可能性がある競合の可能性がなくなります。  
  
 ClickOnce の配置を作成する方法についてのステップ バイ ステップ`<useManifestForTrust>`有効になっているを参照してください[チュートリアル: ClickOnce アプリケーションはありません必要な設定を指定の手動展開とその保持のブランド化情報](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>実行時に信頼 Works 用のアプリケーション マニフェスト  
 実行時に、アプリケーション マニフェストを使用して、信頼のためのしくみをよく理解するを取得するには、次の例を検討してください。 Microsoft .NET Framework 3.5 を対象とする ClickOnce アプリケーションを作成します。 アプリケーション マニフェストを使用して、`<useManifestForTrust>`要素と、Microsoft によって署名されています。 Adventure Works 自己署名証明書を使用して、配置マニフェストに署名します。 Adventure Works クライアントは Microsoft によって署名されたアプリケーションを信頼するように構成します。  
  
 ユーザーは、配置マニフェストへのリンクをクリックすると、ClickOnce は、ユーザーのコンピューターにアプリケーションをインストールします。 証明書と展開に関する情報は、一意にクライアント コンピューターで ClickOnce アプリケーションを識別します。 ユーザーが別の場所から、同じアプリケーションを再度インストールしようとすると、ClickOnce はこの id を使用、クライアントで、アプリケーションが既にが存在することを確認します。  
  
 次に、ClickOnce は ClickOnce を許可する信頼のレベルを決定するアプリケーション マニフェストの署名に使用される、Authenticode 証明書を調べます。 Adventure Works は、Microsoft によって署名されたアプリケーションを信頼するには、そのクライアントを構成したので、この ClickOnce アプリケーションには完全な信頼が付与されます。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>以前のバージョンの顧客展開を作成します。  
 場合、開発者が展開しようと ClickOnce アプリケーションの .NET Framework の旧バージョンを使用しているユーザーにしますか。 次のセクションでは、長所と短所の各と共に、いくつかの推奨されるソリューションを要約します。  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>お客様に代わって配置に署名します。  
 1 つの可能な展開戦略は、お客様の秘密キーを使用して、お客様の代わりの展開に署名するためのメカニズムを作成する開発者です。 これにより、開発者が秘密キーまたは複数の展開パッケージを管理する必要がなくなります。 開発者は、各顧客にだけ、同じデプロイを提供します。 署名サービスを使用して各自の環境用にカスタマイズするお客様の責任です。  
  
 このメソッドの 1 つの欠点は、時間とそれを実装するために必要な費用です。 このようなサービスは、.NET Framework SDK に付属のツールを使用して構築できるは、開発時間が増加を製品ライフ サイクルに追加します。  
  
 前述したこのトピックの前に、別の欠点は、各顧客のバージョンのアプリケーションが競合する可能性がありますの同じアプリケーション id を持つです。 これに問題がある場合、開発者はアプリケーションごとに一意の名前に、配置マニフェストを生成するときに使用される名前 フィールドを変更できます。 アプリケーションのバージョンごとに個別の id を作成され、潜在的な id が競合が排除されます。 このフィールドに対応して、 `-Name` Mage.exe、ために、引数、**名前**フィールドに、**名前**MageUI.exe でタブです。  
  
 たとえば、開発者がアプリケーション 1 をという名前のアプリケーションを作成するとします。 アプリケーション 1 に設定名 フィールドを使用して単一の展開を作成するのではなく、開発者はこの名前は、Application1 裁量、Application1 CustomerB などの顧客固有のバリエーションのいくつかの展開を作成しなどできます。  
  
### <a name="deploy-using-a-setup-package"></a>セットアップ パッケージを使用した展開します。  
 2 番目の可能な展開方法では、ClickOnce アプリケーションの最初の展開を実行する Microsoft セットアップ プロジェクトを生成します。 これは、複数の異なる形式のいずれかで指定することができます。 セットアップの実行可能ファイルとして、MSI 展開として (です。EXE)、またはバッチ スクリプトと共にキャビネット (.cab) ファイルとして。  
  
 この手法を使用して、開発者は、顧客を含む、アプリケーション ファイル、アプリケーション マニフェストおよび配置マニフェストをテンプレートとして機能する展開できます。 顧客もプロンプトが表示デプロイメント URL (サーバーまたはファイル共有のユーザーが ClickOnce アプリケーションをインストールする場所) にデジタル証明書とセットアップ プログラムを実行しました。 セットアップ アプリケーションは、更新チェック間隔など、追加 ClickOnce 構成オプションの入力を求めるにもできます。 セットアップ プログラムはこの情報を収集すると、実際の配置マニフェストを生成し、署名し、指定されたサーバーの場所に ClickOnce アプリケーションを発行します。  
  
 このような状況で配置マニフェストの署名をお客様に、次の 3 つの方法があります。  
  
1.  お客様は、証明機関 (CA) によって発行された有効な証明書を使用できます。  
  
2.  このアプローチをバリエーションとして、顧客は、自己署名証明書を使用して配置マニフェストに署名を選択できます。 この場合の欠点は、アプリケーションをインストールするかどうかをユーザーに確認するときに「不明な発行元」という言葉を表示になります。 ただし、利点は、時間と、証明機関によって発行された証明書に必要なコストを費やすことの小規模なお客様は阻止することです。  
  
3.  最後に、開発者は、セットアップ パッケージに独自の自己署名証明書を含めることができます。 これにより、このトピックの前半で説明したアプリケーション id を持つ可能性のある問題が発生します。  
  
 配置プロジェクトのセットアップ方法の欠点は、時間と展開のカスタム アプリケーションを構築するために必要な費用です。  
  
### <a name="have-customer-generate-deployment-manifest"></a>顧客配置マニフェストを生成  
 3 番目の可能な展開戦略に渡す、アプリケーション ファイルとアプリケーション マニフェスト off、顧客にです。 このシナリオでは、お客様は、.NET Framework SDK を使用して生成し、配置マニフェストに署名する担当します。  
  
 この方法の欠点は、.NET Framework SDK ツールをインストールして、開発者またはシステム管理者には、これらを使用できるスキルを持ったがある顧客を必要とすることです。 一部のお客様は、自身の一部でほとんどまたはまったくの技術的な労力を必要とするソリューションを要求可能性があります。  
  
## <a name="see-also"></a>参照  
 [ClickOnce アプリケーションのテストの配置と再署名なしの実稼働サーバー](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [チュートリアル : 再署名が不要で商標を保持する ClickOnce アプリケーションの手動配置](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)