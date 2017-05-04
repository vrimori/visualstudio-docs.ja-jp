---
title: "方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "インストール (Visual Studio の Office 開発ツールを)"
  - "Office ランタイム [Visual Studio での Office 開発]"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# 方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の Microsoft Office Developer Tools を使用して作成したソリューションを実行するには、各コンピューターに Visual Studio 2010 Tools for Office Runtime がインストールされている必要があります。  ランタイムは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、および Microsoft Office をインストールすると自動的にインストールされます。  詳細については、「[Visual Studio Tools for Office ランタイムのインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)」を参照してください。  
  
 次の場合は、手動による以下のインストール手順を実行する必要があります。  
  
-   [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をサーバーにインストールする必要がある場合。  たとえば、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用してサーバー上のドキュメント レベルのソリューションを管理する場合があります。  
  
-   Office ソリューションのその他の必須コンポーネントが既にインストールされているコンピューターにランタイムをインストールする必要がある場合。  
  
    > [!NOTE]  
    >  .NET Framework および [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールするには、開発コンピューターの管理者である必要があります。  
  
### Visual Studio Tools for Office ランタイムをインストールするには  
  
1.  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をインストールします。  
  
    -   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] をダウンロードする場合は、「[Microsoft .NET Framework 4 \(Web インストーラー\)](http://go.microsoft.com/fwlink/?LinkId=178957)」を参照してください。  
  
    -   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] をダウンロードする場合は、「[Microsoft .NET Framework 4 Client Profile \(Web インストーラー\)](http://go.microsoft.com/fwlink/?LinkId=178958)」を参照してください。  
  
    -   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] をダウンロードする場合は、「[Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)」を参照してください。  
  
2.  vstor\_redist.exe を実行して [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールします。  
  
     これらのセットアップ ファイルは「[Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384)」からダウンロードできます。  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の必須コンポーネントは .NET Framework の場合と同じです。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、言語パックが用意されています。  Windows のインストールが英語以外の言語に設定されている場合、Windows と同じ言語でランタイム メッセージを表示できます。  同様に、エンド ユーザーが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールし、英語以外の言語に設定されている Windows のインストールでソリューションを実行すると、Windows と同じ言語でランタイム メッセージが表示されます。  場合によっては、追加の言語パックが必要になる場合があります。  たとえば、Windows で複数の言語設定が使用されている場合や、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] のインストール後に別の言語に切り替える場合に、追加の言語パックが必要になる場合があります。  言語パックは、「[Microsoft Visual Studio 2010 Tools for Office Language Pack \(バージョン 4.0 ランタイム\)](http://go.microsoft.com/fwlink/?LinkId=140386)」からアクセスできます。  
  
## 参照  
 [はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office ソリューションを開発できるようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [方法: Office ソリューションを開発できるようにコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [方法 : Office のプライマリ相互運用機能アセンブリをインストールする](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [ServerDocument クラスによるサーバー上のドキュメントの管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  