---
title: "How to: Add a Custom SharePoint Node to Server Explorer"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードにはカスタム ノードを追加できます。  既定では**サーバー エクスプローラー**に表示されない SharePoint サイトのコンポーネントを別途表示する必要がある場合に便利な方法です。  詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。  
  
 カスタム ノードを追加するには、まず、新しいノードを定義するクラスを作成します。  次に、そのノードを既存のノードの子として追加する拡張機能を作成します。  
  
### 新しいノードを定義するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  この属性によって、Visual Studio で <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> の実装を検出し、読み込むことができます。  この属性のコンストラクターには <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 型を渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  ノードを定義する際は、新しいノードの文字列識別子をこの属性によって指定します。  ノードの識別子が重複しないよう、「*\<会社名\>*.*\<ノード名\>*」という形式を使用することをお勧めします。  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> メソッドの実装では、*typeDefinition* パラメーターのメンバーを使用して、新しいノードの動作を構成します。  このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> インターフェイスに定義されているイベントにアクセスできるようにする <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> オブジェクトです。  
  
     新しいノードを定義する方法を次のコード例に示します。  この例は、プロジェクトに CustomChildNodeIcon という名前のアイコンが埋め込みリソースとして含まれていることを前提としています。  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### 既存のノードの子として新しいノードを追加するには  
  
1.  ノード定義と同じプロジェクトで、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装するクラスを作成します。  
  
2.  クラスに <xref:System.ComponentModel.Composition.ExportAttribute> 属性を追加します。  この属性によって、Visual Studio で <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> の実装を検出し、読み込むことができます。  この属性のコンストラクターに <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 型を渡します。  
  
3.  クラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 属性を追加します。  ノードの拡張機能では、拡張するノードの型の文字列識別子をこの属性によって指定します。  
  
     Visual Studio に用意されている組み込みのノード型を指定するには、この属性のコンストラクターに次のいずれかの列挙値を渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: これらの値を使用して、**サーバー エクスプローラー**のサイト接続ノード \(サイトの URL を表示するノード\)、サイト ノード、またはその他のすべての親ノードを指定します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: これらの値を使用して、リスト、フィールド、コンテンツの種類を表すノードなど、SharePoint サイトの個々のコンポーネントを表す組み込みのノードの 1 つを指定します。  
  
4.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> メソッドの実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> パラメーターの <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> イベントを処理します。  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> イベント ハンドラーで、イベント引数パラメーターで公開されている <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> オブジェクトの子ノード コレクションに新しいノードを追加します。  
  
     次のコード例は、**サーバー エクスプローラー**で SharePoint サイト ノードの子として新しいノードを追加する方法を示します。  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## コード例全体  
 次のコード例は、単純なノードを定義し、**サーバー エクスプローラー**で SharePoint サイト ノードの子として追加する方法を示す完成したコードです。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## コードのコンパイル  
 この例は、プロジェクトに CustomChildNodeIcon という名前のアイコンが埋め込みリソースとして含まれていることを前提としています。  また、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## 拡張機能の配置  
 **サーバー エクスプローラー**の拡張機能を配置するには、同梱する必要のあるアセンブリや各種ファイルの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  