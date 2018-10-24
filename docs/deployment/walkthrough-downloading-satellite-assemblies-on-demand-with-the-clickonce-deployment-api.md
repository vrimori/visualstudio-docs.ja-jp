---
title: 'チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリのダウンロード |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 506495f8be0b552f35bed0610e9fb43a77efb151
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883030"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードします。
サテライト アセンブリを使用すると、複数のカルチャに対して Windows フォーム アプリケーションを構成できます。 *サテライト アセンブリ* とは、アプリケーションの既定のカルチャ以外のカルチャ用アプリケーション リソースを含むアセンブリのことです。  
  
 説明したよう[ローカライズ ClickOnce アプリケーション](../deployment/localizing-clickonce-applications.md)、同じ内に複数のカルチャ用の複数のサテライト アセンブリを含めることができます[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 既定では、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] により配置に含まれるすべてのサテライト アセンブリがクライアント コンピューターにダウンロードされます。ただし、多くの場合、1 つのクライアントに必要なサテライト アセンブリは 1 つだけです。  
  
 このチュートリアルでは、サテライト アセンブリをオプションとしてマークする方法、および現在のカルチャ設定にクライアント コンピューターが必要とするアセンブリのみをダウンロードする方法について説明します。 次の手順では、 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]から入手できるツールを使用します。 このタスクを、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用して実行することもできます。  参照してください[チュートリアル: ClickOnce 配置デザイナーを使用して API で必要に応じてサテライト アセンブリをダウンロード](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110))または[チュートリアル: ClickOnce 配置 API を使用して必要に応じてサテライト アセンブリをダウンロードデザイナー](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120))します。  
  
> [!NOTE]
>  次のコード例は、テストを目的としているため、プログラム内でカルチャを `ja-JP`に設定しています。 このコードを運用環境用に調整する方法については、このトピックの「次の手順」セクションを参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、ローカライズされたリソースを、Visual Studio を使用してアプリケーションに追加する方法を理解していることを想定しています。 詳細については、次を参照してください。[チュートリアル: ローカライズの Windows フォーム](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))します。  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>必要に応じてサテライト アセンブリをダウンロードするには  
  
1. アプリケーションに次のコードを追加して、サテライト アセンブリのオンデマンドでのダウンロードを有効にします。  
  
    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2. 使用して、アプリケーションのサテライト アセンブリを生成[Resgen.exe (リソース ファイル ジェネレーター)](/dotnet/framework/tools/resgen-exe-resource-file-generator)または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
3. アプリケーション マニフェストを生成またはを使用して、既存のアプリケーション マニフェストを開く*MageUI.exe*します。 このツールの詳細については、次を参照してください。 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)します。  
  
4. **[Files]** タブをクリックします。  
  
5. をクリックして、**省略記号**ボタン (**.**) のすべてのアプリケーションのアセンブリとを使用して生成したサテライト アセンブリを含むファイルを含むディレクトリを選択して*Resgen.exe*します。 (サテライト アセンブリは、フォームで、名前を持ちます *\<isoCode > \ApplicationName.resources.dll*ここで、 \<isoCode > は RFC 1766 形式の言語識別子です)。  
  
6. **[作成]** をクリックして、配置にファイルを追加します。  
  
7. 各サテライト アセンブリの **[省略可能]** チェック ボックスをオンにします。  
  
8. 各サテライト アセンブリの [グループ] フィールドに ISO 言語識別子を設定します。 たとえば、日本語のサテライト アセンブリであれば、ダウンロード グループ名として「 `ja-JP`から入手できるツールを使用します。 これにより、ユーザーの <xref:System.Threading.Thread.CurrentUICulture%2A> プロパティの設定に応じて該当するサテライト アセンブリをダウンロードする、手順 1 で追加したコードが有効になります。  
  
## <a name="next-steps"></a>次の手順  
 コード例を見ると、 <xref:System.Threading.Thread.CurrentUICulture%2A> が特定の値に設定されています。しかし、運用環境では、クライアント コンピューターに適切な値が既定で設定されるため、この行は削除する必要があります。 たとえば、アプリケーションを日本語のクライアント コンピューターで実行する場合、既定では <xref:System.Threading.Thread.CurrentUICulture%2A> が `ja-JP` になります。 ここでは、アプリケーションの配置前にサテライト アセンブリをテストするという趣旨でプログラムから値を設定しています。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションをローカライズします。](../deployment/localizing-clickonce-applications.md)