---
title: "方法: for Office Runtime の再頒布可能パッケージの Visual Studio Tools のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: "94"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cdd4ab2331bb6e21c126f10258db2e233a533f9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする
  Microsoft Office developer tools を使用して作成したソリューションを実行する各コンピューターに Visual Studio 2010 Tools for Office Runtime をインストールする必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 ランタイムは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、および Microsoft Office をインストールすると自動的にインストールされます。 詳細については、「 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)」を参照してください。  
  
 次の場合は、手動による以下のインストール手順を実行する必要があります。  
  
-   [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をサーバーにインストールする必要がある場合。 たとえば、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用してサーバー上のドキュメント レベルのソリューションを管理する場合があります。  
  
-   Office ソリューションのその他の必須コンポーネントが既にインストールされているコンピューターにランタイムをインストールする必要がある場合。  
  
    > [!NOTE]  
    >  .NET Framework および [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールするには、開発コンピューターの管理者である必要があります。  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイムをインストールするには  
  
1.  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をインストールします。  
  
    -   ダウンロードする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を参照してください[Microsoft .NET Framework 4 (Web インストーラー)](http://go.microsoft.com/fwlink/?LinkId=178957)です。  
  
    -   ダウンロードする、[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]を参照してください[Microsoft .NET Framework 4 Client Profile (Web インストーラー)](http://go.microsoft.com/fwlink/?LinkId=178958)です。  
  
    -   ダウンロードする、[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を参照してください[Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)です。  
  
2.  vstor_redist.exe を実行して [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールします。  
  
     これらのセットアップ ファイルをダウンロードする[Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384)です。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の必須コンポーネントは .NET Framework の場合と同じです。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]言語パックが含まれています。 Windows のインストールが英語以外の言語に設定されている場合、Windows と同じ言語でランタイム メッセージを表示できます。 同様に、エンド ユーザーが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールし、英語以外の言語に設定されている Windows のインストールでソリューションを実行すると、Windows と同じ言語でランタイム メッセージが表示されます。 場合によっては、追加の言語パックが必要になる場合があります。 たとえば、Windows のコピーが複数の言語設定を使用して、または既にインストールされている後に別の言語に切り替えるを使用する追加の言語パックを必要があります、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。 言語パックを検索できる[Microsoft Visual Studio の 2010 Tools for Microsoft Office System (バージョン 4.0 ランタイム) Language Pack](http://go.microsoft.com/fwlink/?LinkId=140386)です。  
  
## <a name="see-also"></a>参照  
 [作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [方法: Office ソリューションを開発コンピューターを構成します。](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [方法: Office プライマリ相互運用機能アセンブリをインストール](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  