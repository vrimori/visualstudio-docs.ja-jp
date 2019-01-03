---
title: '方法: Visual Studio Tools for Office ランタイム再頒布可能パッケージのインストールします。'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f9267e340d62def2660f807670dc9804dd531c8f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988768"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>方法: Visual Studio Tools for Office ランタイム再頒布可能パッケージのインストールします。
  Microsoft Office developer tools を使用して作成したソリューションを実行する各コンピューターで、Visual Studio 2010 Tools for Office ランタイムをインストールする必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 ランタイムは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、および Microsoft Office をインストールすると自動的にインストールされます。 詳細については、次を参照してください。 [Visual Studio Tools for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)します。  
  
 次の場合は、手動による以下のインストール手順を実行する必要があります。  
  
-   [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をサーバーにインストールする必要がある場合。 たとえば、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用してサーバー上のドキュメント レベルのソリューションを管理する場合があります。  
  
-   Office ソリューションのその他の必須コンポーネントが既にインストールされているコンピューターにランタイムをインストールする必要がある場合。  
  
    > [!NOTE]  
    >  .NET Framework および [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールするには、開発コンピューターの管理者である必要があります。  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイムをインストールするには  
  
1.  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をインストールします。  
  
    -   ダウンロードする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を参照してください[Microsoft .NET Framework 4 (Web インストーラー)](http://go.microsoft.com/fwlink/?LinkId=178957)します。  
  
    -   ダウンロードする、[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]を参照してください[Microsoft .NET Framework 4 Client Profile (Web インストーラー)](http://go.microsoft.com/fwlink/?LinkId=178958)します。  
  
    -   ダウンロードする、[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を参照してください[Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)します。  
  
2.  実行*vstor_redist.exe*をインストールする、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。  
  
     これらのセットアップ ファイルをダウンロードする[Visual Studio 2010 Tools for Office ランタイム](http://go.microsoft.com/fwlink/?LinkId=140384)します。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の必須コンポーネントは .NET Framework の場合と同じです。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]言語パックが含まれています。 Windows のインストールが英語以外の言語に設定されている場合、Windows と同じ言語でランタイム メッセージを表示できます。 同様に、エンド ユーザーが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールし、英語以外の言語に設定されている Windows のインストールでソリューションを実行すると、Windows と同じ言語でランタイム メッセージが表示されます。 場合によっては、追加の言語パックが必要になる場合があります。 たとえば、既にインストールした後に、別の言語に切り替えることも、Windows のコピーが 1 つ以上の言語設定を使用してを使用する追加の言語パックを必要があります、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 言語パックを検索する[Microsoft Visual Studio の 2010 Tools for Microsoft Office system (バージョン 4.0 ランタイム) language pack](http://go.microsoft.com/fwlink/?LinkId=140386)します。  
  
## <a name="see-also"></a>関連項目  
 [開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office ソリューションを開発コンピューターを構成します。](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [方法: Office ソリューションを開発コンピューターを構成します。](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [方法: Office プライマリ相互運用機能アセンブリをインストールします。](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)  
