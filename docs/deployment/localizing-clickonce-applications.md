---
title: ClickOnce アプリケーションのローカライズ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3d7ebc762c7b1feb895323f7ef9ee0180ce954e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="localizing-clickonce-applications"></a>ClickOnce アプリケーションのローカライズ
ローカライズは、アプリケーションを特定のカルチャに適したものにするためのプロセスです。 このプロセスには、ユーザー インターフェイス (UI) のテキストを地域固有の言語に翻訳する作業、正しい日付と通貨の書式の適用、フォーム上にあるコントロールのサイズの調整、およびコントロールを右から左へとミラー化する作業 (必要な場合) が含まれます。  
  
 アプリケーションをローカライズすると、1 つ以上のサテライト アセンブリが作成されます。 各アセンブリには、特定のカルチャに固有の UI 文字列、画像、およびその他のリソースが含まれます (アプリケーションのメインの実行可能ファイルには、アプリケーションの既定のカルチャに対応する文字列が含まれています)。  
  
 ここでは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを他のカルチャ向けに配置する 3 つの方法について説明します。  
  
-   すべてのサテライト アセンブリを 1 つの配置に含める。  
  
-   カルチャごとに 1 つの配置を生成し、それぞれに 1 つのサテライト アセンブリを含める。  
  
-   必要に応じてサテライト アセンブリをダウンロードする。  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>すべてのサテライト アセンブリを 1 つの配置に含める  
 複数の [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を発行するのではなく、すべてのサテライト アセンブリを含む 1 つの [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を発行します。  
  
 これは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での既定の方法です。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でこの方法を使用する場合、追加の作業を実行する必要はありません。  
  
 MageUI.exe でこのメソッドを使用するに、アプリケーションのカルチャを設定する必要があります**ニュートラル**MageUI.exe でします。 次に、すべてのサテライト アセンブリを手動で配置に含める必要があります。 MageUI.exe を使用して、サテライト アセンブリを追加することができます、 **Populate**のボタンでは、**ファイル**アプリケーション マニフェストのタブです。  
  
 この方法の利点は、単一の配置が作成されるので、配置のローカライズが簡素化されることです。 実行時に、ユーザーが使用する Windows オペレーティング システムの既定のカルチャに応じて、適切なサテライト アセンブリが使用されます。 この方法の欠点は、クライアント コンピューターでアプリケーションをインストールまたは更新するたびに、すべてのサテライト アセンブリがダウンロードされることです。 このため、アプリケーションに大量の文字列が含まれている場合や顧客が使用するネットワーク接続の速度が遅い場合は、このプロセスがアプリケーション更新時のパフォーマンスに影響を与える可能性があります。  
  
> [!NOTE]
>  この方法では、それぞれのカルチャで異なるテキスト文字列のサイズに対応するために、コントロールの高さ、幅、および位置をアプリケーションが自動的に調整することを前提としています。 Windows フォームには、容易にローカライズできるフォームをデザインするためのさまざまなコントロールとテクノロジが用意されています。これには、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールと <xref:System.Windows.Forms.TableLayoutPanel> コントロール、および <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが含まれます。  参照してください[する方法: Windows フォームを使用して AutoSize と TableLayoutPanel コントロールでサポート ローカリゼーション](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))です。  
  
## <a name="generate-one-deployment-for-each-culture"></a>カルチャごとに 1 つの配置を生成する  
 この配置ストラテジでは、複数の配置を生成します。 各配置には特定のカルチャに必要なサテライト アセンブリのみを含め、その配置をそのカルチャ固有としてマークします。  
  
 このメソッドを使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、設定、**発行の言語**プロパティを**発行**目的の地域にタブです。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、選択した地域に必要なサテライト アセンブリを自動的に組み込み、それ以外のすべてのサテライト アセンブリを配置から除外します。  
  
 この作業は、Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] の MageUI.exe ツールを使用して実行することもできます。 使用して、 **Populate**のボタンでは、**ファイル**アプリケーション ディレクトリから他のすべてのサテライト アセンブリを除外し、設定、アプリケーション マニフェストのタブ、**カルチャ**フィールドに、**名前**MageUI.exe で配置マニフェストのタブです。 この手順によって、正しいサテライト アセンブリが組み込まれるだけでなく、配置マニフェストに含まれる `assemblyIdentity` 要素の `language` 属性が、対応するカルチャに設定されます。  
  
 アプリケーションを発行した後、アプリケーションがサポートする追加のカルチャごとにこの手順を繰り返す必要があります。 発行するようにして別の Web サーバー ディレクトリまたはファイル共有ディレクトリに常に、各アプリケーション マニフェストで異なるサテライト アセンブリを参照し、各配置マニフェストは、に別の値が行う必要があります`language`属性。  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>サテライト アセンブリを必要に応じてダウンロードする  
 すべてのサテライト アセンブリを 1 つの配置に含める場合は、オンデマンド ダウンロードを使用し、サテライト アセンブリをオプションとしてマークすることにより、パフォーマンスを高めることができます。 マークしたアセンブリは、アプリケーションがインストールまたは更新されるときにはダウンロードされません。 これらのアセンブリは、必要になったときに <xref:System.Deployment.Application.ApplicationDeployment> クラスの <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> メソッドを呼び出すことでインストールできます。  
  
 サテライト アセンブリを必要に応じてダウンロードする処理は、その他の種類のアセンブリを必要に応じてダウンロードする処理と若干異なります。 使用して、このシナリオを有効にする方法の詳細情報とコード例については、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]用ツールの[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を参照してください[チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)です。  
  
 このシナリオは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で有効にすることもできます。  「 [チュートリアル: デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) 」または「 [チュートリアル: デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする](http://msdn.microsoft.com/library/ms366788\(v=vs.120\))」もご覧ください。  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>ローカライズされた ClickOnce アプリケーションを配置前にテストする  
 サテライト アセンブリが Windows フォーム アプリケーションに使用されるのは、アプリケーションのメイン スレッドの <xref:System.Threading.Thread.CurrentUICulture%2A> プロパティがそのサテライト アセンブリのカルチャに設定されている場合に限られます。 各地域の顧客は Windows のローカライズ版を既に実行していると考えられるため、カルチャも該当する既定値に設定されているはずです。  
  
 アプリケーションを顧客が使用できるようにする前に、ローカライズされた配置をテストするには、次の 3 つのオプションがあります。  
  
-   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを、Windows の該当するローカライズ版で実行する。  
  
-   アプリケーション内で、<xref:System.Threading.Thread.CurrentUICulture%2A> プロパティをプログラムにより設定する (このプロパティは、<xref:System.Windows.Forms.Application.Run%2A> メソッドを呼び出す前に設定する必要があります)。  
  
## <a name="see-also"></a>関連項目  
 [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [Windows フォームのグローバル化](/dotnet/framework/winforms/advanced/globalizing-windows-forms)