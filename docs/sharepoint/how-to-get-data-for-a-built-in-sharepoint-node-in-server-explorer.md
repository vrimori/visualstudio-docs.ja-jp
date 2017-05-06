---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  **サーバー エクスプローラー**の組み込みの SharePoint ノードごとに、そのノードが表す SharePoint コンポーネント \(基になるコンポーネント\) のデータを取得できます。  詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。  
  
## 例  
 次のコード例は、**サーバー エクスプローラー**でリスト ノードが表す SharePoint リスト \(基になるリスト\) のデータを取得する方法を示しています。  既定では、リスト ノードには **\[ブラウザーで表示\]** コンテキスト メニュー項目があり、この項目をクリックすると、Web ブラウザーでリストを開くことができます。  この例では、Visual Studio でリストを直接開く **\[Visual Studio で表示\]** コンテキスト メニュー項目を追加して、リスト ノードを拡張します。  また、ノードのリスト データにアクセスして、Visual Studio で開くリストの URL を取得します。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、Visual Studio でリストを開くために使用する <xref:EnvDTE.DTE> オブジェクトを取得します。  SharePoint プロジェクト サービスの詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
 SharePoint ノードの拡張機能を作成する場合の基本的な作業の詳細については、「[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)」を参照してください。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 **サーバー エクスプローラー**の拡張機能を配置するには、同梱する必要のあるアセンブリや各種ファイルの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  