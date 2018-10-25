---
title: ClickOnce アプリケーションをデプロイする他のユーザーの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b74e8a988505c5386b444df27f7726a8ceb51a62
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870781"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>ClickOnce アプリケーションをデプロイする他のユーザーの作成します。
ClickOnce 配置を作成しているすべての開発者は、アプリケーション自体を展開する予定です。 それらの多くは、ClickOnce を使用してアプリケーションをパッケージし、し、ファイルを大企業など、お客様に渡します。 お客様は、そのネットワーク上のアプリケーションをホストする役割の 1 つになります。 このトピックでは、.NET Framework バージョン 3.5 より前のバージョンでは、このような展開に固有の問題について説明します。 .NET Framework 3.5 の新しい「信頼のマニフェストを使用して、」機能を使用して新しい解決し、について説明します。 最後に、まだ .NET Framework の以前のバージョンを使用しているお客様の場合、ClickOnce 配置を作成するための推奨される方法で終了します。  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>お客様の展開の作成に関連する問題  
 いくつかの問題は、顧客に配置を指定することを計画するときに発生します。 最初の問題は、コード署名に関するものです。 ネットワーク全体に配置するために、配置マニフェストとアプリケーション マニフェストの ClickOnce 配置する必要があります両方で署名するデジタル証明書。 これは、マニフェストに署名するときに、開発者の証明書または顧客の証明書を使用するかどうかの質問を発生させます。  
  
 使用する証明書の問題は、ClickOnce アプリケーションの id は、配置マニフェストのデジタル署名に基づいてとして重要、です。 場合は、開発者は、配置マニフェストに署名、ことでした競合が発生する顧客は、大企業、および会社の 1 つ以上の部門がカスタマイズされたバージョンのアプリケーションをデプロイします場合、。  
  
 たとえば、Adventure Works が財務部門と人事部門を持つことがあるとします。 両方の部門が SQL database に格納されたデータからレポートを生成する Microsoft Corporation からの ClickOnce アプリケーションのライセンスを取得します。 Microsoft では、各部門にそのデータ用にカスタマイズされているアプリケーションのバージョンを提供します。 場合は、アプリケーションは同じ Authenticode 証明書で署名済み、両方のアプリケーションを使用しようとしたユーザーはエラーが発生、ClickOnce には、最初と同じものとして 2 番目のアプリケーションと考えているとします。 この場合、お客様は、予測不可能な望ましくない副作用を含む、アプリケーションでローカルに格納されているデータの損失を発生する可能性があります。  
  
 その他の問題に関連コードの署名は、 `deploymentProvider` ClickOnce アプリケーションの更新プログラムを検索する場所を指示する配置マニフェスト内の要素。 この要素は、それに署名する前に、配置マニフェストに追加する必要があります。 この要素は後で追加された、配置マニフェストが再署名する必要があります。  
  
### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>配置マニフェストに署名する必要があります。  
 一意でない展開のこの問題を解決は開発者がアプリケーション マニフェスト、署名し、お客様が配置マニフェストに署名します。 このアプローチは、その他の問題が導入されています。 Authenticode 証明書は、保護された資産を維持する必要があります、ため、顧客が開発者は配置に署名する証明書を与えることはできませんだけです。 お客様は、配置マニフェストに署名自体、.NET Framework SDK を自由に使用できるツールを使用して、中に顧客は、または処理を提供できるものよりも詳細な技術知識が必要です。 開発者、このような場合、アプリケーション、Web サイト、または顧客がアプリケーションに署名するためのバージョンを送信する他のメカニズムが通常作成します。  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>ClickOnce アプリケーションのセキュリティ署名の顧客の影響  
 場合でも、開発者とお客様の顧客がアプリケーション マニフェストに署名する必要があります同意すると、この信頼されたアプリケーションの展開に適用されるように特にをアプリケーションの id を囲んでいるその他の問題を発生させます。 (この機能の詳細については、次を参照してください[信頼されたアプリケーション展開の概要](../deployment/trusted-application-deployment-overview.md)。)。Adventure Works は、それらを Microsoft Corporation によって提供される任意のアプリケーションの完全な信頼で実行されるように、クライアント コンピューターを構成する必要があるとします。 Adventure Works は、配置マニフェストに署名する場合、ClickOnce は、アプリケーションの信頼レベルを決定する Adventure Work のセキュリティ署名が使用されます。  
  
## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>信頼のアプリケーション マニフェストを使用して、顧客の展開を作成します。  
 .NET Framework 3.5 では、ClickOnce には、マニフェストの署名方法のシナリオに、新しいソリューションで開発者やお客様が提供する新しい機能が含まれています。 ClickOnce アプリケーション マニフェストは、という名前の新しい要素をサポートしている`<useManifestForTrust>`を示すアプリケーション マニフェストのデジタル署名は、どのような信頼の決定を行うために使用する必要がありますが、開発者ができるようにします。 開発者が ClickOnce パッケージ化ツールを使用 — など*Mage.exe*、 *MageUI.exe*、および Visual Studio-、アプリケーション マニフェストにこの要素を含めるだけでなく、発行元名の両方を埋め込むとマニフェストにアプリケーションの名前。  
  
 使用する場合`<useManifestForTrust>`、配置マニフェストは、証明機関によって発行された、Authenticode 証明書で署名する必要はありません。 代わりに、自己署名証明書と呼ばれるものを署名することができます。 自己署名証明書では、標準の .NET Framework SDK ツールを使用してお客様、または開発者によって生成され、標準の ClickOnce 配置ツールを使用して、配置マニフェストに適用されます。 詳細については、次を参照してください。 [MakeCert](/windows/desktop/SecCrypto/makecert)します。  
  
 配置マニフェストに自己署名証明書を使用するには、いくつかの利点について説明します。 によって、顧客を取得または独自の Authenticode 証明書を作成する必要がなくなるため`<useManifestForTrust>`開発者は、アプリケーションで独自のブランド id を維持しながら、顧客の展開を簡略化します。 安全なは、一意のアプリケーション id が設定されている署名付きの展開の組み合わせになります。 これにより、複数の顧客に同じアプリケーションを配置からなる可能性がある潜在的な競合がなくなります。  
  
 ClickOnce 配置とを作成する方法についての詳細な手順について`<useManifestForTrust>`有効になっているを参照してください[チュートリアル: 再署名が要求されるされないのブランド情報を保持するClickOnceアプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>実行時の信頼のアプリケーション マニフェストのしくみ  
 実行時にアプリケーション マニフェストを使用して、信頼のためのしくみの理解を深めるを取得するには、次の例を検討します。 .NET Framework 3.5 を対象とする ClickOnce アプリケーションは、Microsoft によって作成されます。 アプリケーション マニフェストを使用して、`<useManifestForTrust>`要素と、Microsoft によって署名されています。 Adventure Works 自己署名証明書を使用して、配置マニフェストに署名します。 Adventure Works クライアントは、Microsoft によって署名されたすべてのアプリケーションを信頼して構成されます。  
  
 ユーザーは、配置マニフェストへのリンクをクリックすると、ClickOnce は、ユーザーのコンピューターにアプリケーションをインストールします。 証明書と展開の情報は、一意にクライアント コンピューターの ClickOnce アプリケーションを特定します。 ユーザーが別の場所から、同じアプリケーションを再インストールしようとすると、ClickOnce は、既にアプリケーションがクライアントに存在するかを判断するのにこの id を使用できます。  
  
 次に、ClickOnce は、ClickOnce を許可する信頼のレベルを決定するアプリケーション マニフェストに署名するために使用される Authenticode 証明書を調べます。 Adventure Works は、Microsoft によって署名されたアプリケーションを信頼するには、そのクライアントを構成したのでこの ClickOnce アプリケーションは完全な信頼を付与します。 詳細については、次を参照してください。[信頼されたアプリケーション展開の概要](../deployment/trusted-application-deployment-overview.md)します。  
  
## <a name="create-customer-deployments-for-earlier-versions"></a>以前のバージョンの顧客展開を作成します。  
 場合、開発者では、.NET Framework の以前のバージョンを使用しているお客様に ClickOnce アプリケーションを配置はでしょうか。 次のセクションでは、長所と短所の各と共にいくつかの推奨される解決策をまとめたものです。  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>顧客に代わって配置に署名します。  
 1 つの可能な展開戦略は、顧客独自の秘密キーを使用して、お客様に代わって配置に署名するためのメカニズムを作成する開発者。 これにより、開発者が秘密キーまたは複数の展開パッケージを管理する必要がなくなります。 開発者は、各顧客にだけ、同じデプロイを提供します。 署名サービスを使用して、環境をカスタマイズするお客様の責任です。  
  
 このメソッドの 1 つの欠点は、時間とそれを実装するために必要なコストです。 このようなサービス、.NET Framework SDK に付属するツールを使用して、ビルド中には、開発時間が増加を製品のライフ サイクルを追加します。  
  
 このトピックの「別の欠点は、顧客ごとのバージョンのアプリケーションが同一のアプリケーションの id は競合する可能性があります。 これが問題である場合は、開発者はアプリケーションごとに一意の名前に、配置マニフェストを生成するときに使用される名前のフィールドを変更できます。 アプリケーションのバージョンごとに別々 の id が作成され、潜在的な任意の id の競合を取り除くこのが。 このフィールドに対応して、 `-Name` Mage.exe、ために、引数、**名前**フィールドに、**名前**MageUI.exe でタブ。  
  
 たとえば、開発者が Application1 という名前のアプリケーションを作成するとします。 アプリケーション 1 に設定された名前フィールドと 1 つのデプロイを作成する代わりには、開発者はこの名前は、Application1 裁量、Application1 CustomerB などの顧客固有のバリエーションを持つ複数の展開を作成しなど。  
  
### <a name="deploy-using-a-setup-package"></a>セットアップ パッケージを使用してデプロイします。  
 2 番目の考えられる展開方法では、ClickOnce アプリケーションの初期デプロイを実行する Microsoft セットアップ プロジェクトを生成します。 これは、いくつかの異なる形式のいずれかで提供できます。 セットアップの実行可能ファイルとして、MSI 展開として (します。EXE)、またはバッチ スクリプトと共にキャビネット (.cab) ファイルとして。  
  
 この手法を使用して、開発者は、顧客の展開をアプリケーション ファイル、アプリケーション マニフェストおよび配置マニフェスト テンプレートとして機能するが含まれています。 お客様もプロンプトが表示デプロイメント URL (サーバーまたはファイル共有のユーザーが ClickOnce アプリケーションをインストールする場所) のデジタル証明書とセットアップ プログラムを実行します。 セットアップ アプリケーションは、更新プログラムをチェックする間隔など、追加の ClickOnce の構成オプションを要求することもできます。 セットアップ プログラムはこの情報を収集すると、実際の配置マニフェストを生成し、署名し、指定されたサーバーの場所に ClickOnce アプリケーションを発行します。  
  
 次の 3 つの方法が、顧客がこのような状況で配置マニフェストに署名できることがあります。  
  
1. お客様は、証明機関 (CA) によって発行された有効な証明書を使用できます。  
  
2. このアプローチのバリエーション、として、顧客は、自己署名証明書を使用して配置マニフェストに署名を選択できます。 この場合の欠点は、アプリケーションをインストールするかどうかをユーザーに確認するときに、「不明な発行元」という言葉を表示になります。 ただし、利点は、時間と、証明機関によって発行された証明書に必要なコストを費やすことの小規模な顧客は阻止することです。  
  
3. 最後に、開発者は、セットアップ パッケージに独自の自己署名証明書を含めることができます。 これには、このトピックで前述したアプリケーション id、潜在的な問題が導入されています。  
  
   展開プロジェクトのセットアップ メソッドに欠点は、時間とカスタム デプロイ アプリケーションを構築するために必要なコストです。  
  
### <a name="have-customer-generate-deployment-manifest"></a>配置マニフェストを生成しているお客様  
 3 番目の可能な展開戦略を渡すためにはファイルやアプリケーションで顧客にマニフェスト アプリケーションのみをオフします。 このシナリオでは、顧客は、.NET Framework SDK を使用して生成し、配置マニフェストに署名する責任を負います。  
  
 この方法の欠点は、.NET Framework SDK ツールをインストールして、開発者やシステム管理者にそれらを使用してスキルを顧客が必要です。 一部のお客様は、自分では、ほとんどまたはまったくない技術的な作業を必要とするソリューションを要求可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [署名なしの ClickOnce アプリケーションのテストと実稼働サーバーの展開します。](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)   
 [チュートリアル: ClickOnce アプリケーションを手動で展開します。](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [チュートリアル: 再署名不要ブランド情報を保持する ClickOnce アプリケーションを手動で展開します。](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)