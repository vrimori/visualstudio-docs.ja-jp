---
title: "Extending the SharePoint Connections Node in Server Explorer | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  Visual Studio では、開発用コンピューターのローカル SharePoint サイトに**サーバー エクスプローラー** のペインで **SharePoint 接続** ノードを使用して接続できます。  このノードには、ローカル SharePoint サイトのさまざまなコンポーネントが階層型のツリー ビューで表示されます。  たとえば、ローカル サイトのリスト、ドキュメント ライブラリ、およびコンテンツ タイプを表示できます。**サーバー エクスプローラー**を使用してローカルの SharePoint サイトに接続する方法の詳細については、「[サーバー エクスプローラーを使用した SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)」を参照してください。  
  
 **\[SharePoint 接続\]** ノードを拡張するには、既存のノードの拡張機能を作成するか、カスタム ノード型を作成して、それをノードの階層に追加します。  
  
## \[SharePoint 接続\] ノードを拡張するタスク  
 既存のノードを拡張するには、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装する Visual Studio 拡張機能を作成します。  ノードを拡張すると、独自のショートカット メニュー項目やカスタムのプロパティなど、ノードに機能を追加できます。  詳細については、「[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)」を参照してください。  
  
 カスタム ノード型を作成するには、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> インターフェイスを実装する Visual Studio 拡張機能を作成します。  既定では**サーバー エクスプローラー**に表示されない SharePoint サイトのコンポーネントを表示する必要がある場合は、カスタム ノードを作成します。  たとえば、**サーバー エクスプローラー**には、SharePoint サイトの Web パーツ ギャラリーが既定では表示されません。しかし、カスタム ノードを追加することによってそれを実現することができます。  詳細については、「[How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)」および「[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)」を参照してください。  
  
## ノードへのカスタム プロパティの追加  
 ノードを拡張するか、カスタム ノード型を作成すると、そのノードにカスタム プロパティを追加できます。  ノードを選択すると、追加したプロパティが **\[プロパティ\]** ウィンドウに表示されます。  
  
 ノードに追加できるカスタム プロパティには次の 2 種類があります。  
  
-   SharePoint サイトから読み取り専用データのセットを表示するプロパティ。  このデータには、ノードが表す SharePoint コンポーネントが記述されています。  その方法を示すチュートリアルについては、「[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)」を参照してください。  
  
-   カスタムの読み取り\/書き込みデータを表示するプロパティ。  この方法を示すコード例については、「[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)」を参照してください。  
  
## 組み込みノードのデータの取得  
 Visual Studio に用意されているすべての組み込みノードには、それらが表す SharePoint コンポーネントに関するデータが含まれます。  たとえば、SharePoint サイト上でリストを表すノードには、そのリストに関するデータが含まれます。たとえば、リストのタイトルや、既定のビューの URL などです。  
  
 このデータにアクセスするには、目的のノードを表す <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティからデータ オブジェクトを取得します。  データ オブジェクトの型は、ノードの種類によって決まります。  
  
 次のコード例は、リスト ノードのデータ オブジェクトを取得する方法を示します。  この例のコンテキストを確認するには、「[How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)」を参照してください。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 次の表は、各組み込みノードの種類に対するデータ オブジェクトの型の一覧です。  
  
|ノードの種類|データ オブジェクトの型|  
|------------|------------------|  
|SharePoint サイト ノード|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|コンテンツ タイプ|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|機能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Field|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|リスト|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|リスト テンプレート|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|リスト ビュー \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|ワークフロー関連付け|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|ワークフロー テンプレート|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティの使用方法の詳細については、「[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)」を参照してください。  
  
## 参照  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [サーバー エクスプローラーを使用した SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  