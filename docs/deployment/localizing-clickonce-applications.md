---
title: ClickOnce アプリケーションのローカライズ |Microsoft Docs
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
ms.openlocfilehash: 7897869e8cc010d54c1914cbfa8ca763dd3a3bfa
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279343"
---
# <a name="localize-clickonce-applications"></a>ClickOnce アプリケーションをローカライズします。
ローカライズは、アプリケーションを特定のカルチャに適したものにするためのプロセスです。 このプロセスには、ユーザー インターフェイス (UI) のテキストを地域固有の言語に翻訳する作業、正しい日付と通貨の書式の適用、フォーム上にあるコントロールのサイズの調整、およびコントロールを右から左へとミラー化する作業 (必要な場合) が含まれます。  
  
 アプリケーションをローカライズすると、1 つ以上のサテライト アセンブリが作成されます。 各アセンブリには、特定のカルチャに固有の UI 文字列、画像、およびその他のリソースが含まれます (アプリケーションのメインの実行可能ファイルには、アプリケーションの既定のカルチャに対応する文字列が含まれています)。  
  
 ここでは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを他のカルチャ向けに配置する 3 つの方法について説明します。  
  
-   すべてのサテライト アセンブリを 1 つの配置に含める。  
  
-   カルチャごとに 1 つの配置を生成し、それぞれに 1 つのサテライト アセンブリを含める。  
  
-   必要に応じてサテライト アセンブリをダウンロードする。  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>すべてのサテライト アセンブリを 1 つの配置に含める  
 複数の [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を発行するのではなく、すべてのサテライト アセンブリを含む 1 つの [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を発行します。  
  
 これは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での既定の方法です。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でこの方法を使用する場合、追加の作業を実行する必要はありません。  
  
 このメソッドを使用する*MageUI.exe*に、アプリケーションのカルチャを設定する必要があります**ニュートラル**で*MageUI.exe*します。 次に、すべてのサテライト アセンブリを手動で配置に含める必要があります。 *MageUI.exe*を使用してサテライト アセンブリを追加することができます、 **Populate**のボタンでは、**ファイル**アプリケーション マニフェストのタブ。  
  
 この方法の利点は、単一の配置が作成されるので、配置のローカライズが簡素化されることです。 実行時に、ユーザーが使用する Windows オペレーティング システムの既定のカルチャに応じて、適切なサテライト アセンブリが使用されます。 この方法の欠点は、クライアント コンピューターでアプリケーションをインストールまたは更新するたびに、すべてのサテライト アセンブリがダウンロードされることです。 このため、アプリケーションに大量の文字列が含まれている場合や顧客が使用するネットワーク接続の速度が遅い場合は、このプロセスがアプリケーション更新時のパフォーマンスに影響を与える可能性があります。  
  
> [!NOTE]
>  この方法では、それぞれのカルチャで異なるテキスト文字列のサイズに対応するために、コントロールの高さ、幅、および位置をアプリケーションが自動的に調整することを前提としています。 Windows フォームには、容易にローカライズできるフォームをデザインするためのさまざまなコントロールとテクノロジが用意されています。これには、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールと <xref:System.Windows.Forms.TableLayoutPanel> コントロール、および <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが含まれます。  参照してください[方法: AutoSize と TableLayoutPanel コントロールを使用して Windows フォームのローカリゼーションをサポートする](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))します。  
  
## <a name="generate-one-deployment-for-each-culture"></a>カルチャごとに 1 つの展開を生成します。  
 この配置ストラテジでは、複数の配置を生成します。 各配置には特定のカルチャに必要なサテライト アセンブリのみを含め、その配置をそのカルチャ固有としてマークします。  
  
 このメソッドを使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、設定、**発行の言語**プロパティを**発行**目的の地域にタブ。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、選択した地域に必要なサテライト アセンブリを自動的に組み込み、それ以外のすべてのサテライト アセンブリを配置から除外します。  
  
 使用して同じ処理を行うことができます、 *MageUI.exe*ツールでは、Microsoft[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]します。 使用して、 **Populate**のボタンでは、**ファイル**アプリケーション ディレクトリで、その他のすべてのサテライト アセンブリを除外し、設定、アプリケーション マニフェストのタブ、**カルチャ**フィールドに、**名前** タブで、配置マニフェストの*MageUI.exe*します。 この手順によって、正しいサテライト アセンブリが組み込まれるだけでなく、配置マニフェストに含まれる `assemblyIdentity` 要素の `language` 属性が、対応するカルチャに設定されます。  
  
 アプリケーションを発行した後、アプリケーションがサポートする追加のカルチャごとにこの手順を繰り返す必要があります。 発行するようにして別の Web サーバーのディレクトリまたはファイルの共有ディレクトリに常に、各アプリケーション マニフェストは、さまざまなサテライト アセンブリを参照し、各配置マニフェスト、に別の値になりますので、行う必要があります`language`属性。  
  
## <a name="download-satellite-assemblies-on-demand"></a>必要に応じてサテライト アセンブリをダウンロードします。  
 すべてのサテライト アセンブリを 1 つの配置に含める場合は、オンデマンド ダウンロードを使用し、サテライト アセンブリをオプションとしてマークすることにより、パフォーマンスを高めることができます。 マークしたアセンブリは、アプリケーションがインストールまたは更新されるときにはダウンロードされません。 これらのアセンブリは、必要になったときに <xref:System.Deployment.Application.ApplicationDeployment> クラスの <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> メソッドを呼び出すことでインストールできます。  
  
 サテライト アセンブリを必要に応じてダウンロードする処理は、その他の種類のアセンブリを必要に応じてダウンロードする処理と若干異なります。 情報とコードの例を使用してこのシナリオを有効にする方法について、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]用ツールの[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を参照してください[チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロード](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)します。  
  
 このシナリオは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で有効にすることもできます。  参照してください[チュートリアル: ClickOnce 配置 API を使用して、デザイナーで必要に応じてサテライト アセンブリをダウンロード](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110))または[チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードデザイナーを使用して](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120))します。  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>展開する前に、ローカライズされた ClickOnce アプリケーションのテスト  
 サテライト アセンブリが Windows フォーム アプリケーションに使用されるのは、アプリケーションのメイン スレッドの <xref:System.Threading.Thread.CurrentUICulture%2A> プロパティがそのサテライト アセンブリのカルチャに設定されている場合に限られます。 各地域の顧客は Windows のローカライズ版を既に実行していると考えられるため、カルチャも該当する既定値に設定されているはずです。  
  
 アプリケーションを顧客が使用できるようにする前に、ローカライズされた配置をテストするには、次の 3 つのオプションがあります。  
  
-   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを、Windows の該当するローカライズ版で実行する。  
  
-   アプリケーション内で、<xref:System.Threading.Thread.CurrentUICulture%2A> プロパティをプログラムにより設定する (このプロパティは、<xref:System.Windows.Forms.Application.Run%2A> メソッドを呼び出す前に設定する必要があります)。  
  
## <a name="see-also"></a>関連項目  
 [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [Windows フォームのグローバル化します。](/dotnet/framework/winforms/advanced/globalizing-windows-forms)