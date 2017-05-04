---
title: "How to: Extend a SharePoint Node in Server Explorer | Microsoft Docs"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードにノードを拡張できます。  これは、新しい子ノード、ショートカット メニュー項目、またはプロパティを既存のノードに追加するのに役立ちます。  詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。  
  
### サーバー エクスプローラーの SharePoint ノードを拡張するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに <xref:System.ComponentModel.Composition.ExportAttribute> 属性を追加します。  この属性によって、Visual Studio で <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> の実装を検出し、読み込むことができます。  この属性のコンストラクターに <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 型を渡します。  
  
5.  クラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 属性を追加します。  この属性によって、拡張するノードの種類の文字列識別子が指定されます。  
  
     Visual Studio に用意されている組み込みのノード型を指定するには、この属性のコンストラクターに次のいずれかの列挙値を渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: これらの値を使用して、**サーバー エクスプローラー**のサイト接続ノード \(サイトの URL を表示するノード\)、サイト ノード、またはその他のすべての親ノードを指定します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: これらの値を使用して、リスト、フィールド、コンテンツの種類を表すノードなど、SharePoint サイトの個々のコンポーネントを表す組み込みのノードの 1 つを指定します。  
  
6.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> メソッドの実装では、*nodeType* パラメーターのメンバーを使用して、機能をノードに追加します。  このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> インターフェイスに定義されているイベントにアクセスできるようにする <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> オブジェクトです。  たとえば、次のイベントを処理できます。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: このイベントを処理して、新しい子ノードをノードに追加します。  詳細については、「[How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)」を参照してください。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: このイベントを処理して、カスタム ショートカット メニュー項目をノードに追加します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: このイベントを処理して、カスタム プロパティをノードに追加します。  ノードを選択すると、追加したプロパティが **\[プロパティ\]** ウィンドウに表示されます。  
  
## 例  
 次のコード例は、2 種類のノードの拡張機能を作成する方法を示します。  
  
-   コンテキスト メニュー項目を SharePoint サイト ノードに追加する拡張機能  メニュー項目をクリックすると、クリックしたノードの名前が表示されます。  
  
-   **ContosoExampleProperty** という名前のカスタム プロパティを **Body** という名前のフィールドを表す各ノードに追加する拡張機能  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 この拡張機能によって、編集可能な文字列プロパティがノードに追加されます。  また、SharePoint サーバーから読み取り専用データを表示するカスタム プロパティを作成することもできます。  この方法を示す例については、「[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)」を参照してください。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## 拡張機能の配置  
 **サーバー エクスプローラー**の拡張機能を配置するには、同梱する必要のあるアセンブリや各種ファイルの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  