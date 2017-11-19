---
title: "サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張 |Microsoft ドキュメント"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3cf332197227e2055b322bce3658cde66dc48f90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>サーバー エクスプローラーの [SharePoint 接続] ノードの拡張
  使用して Visual Studio で、開発用コンピューターでローカルの SharePoint サイトに接続できる、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウです。 このノードでは、階層ツリー ビューで、ローカルの SharePoint サイトのコンポーネントの多くを表示します。 たとえば、ローカル サイトには、リスト、ドキュメント ライブラリ、およびコンテンツの種類を表示できます。 使用しての詳細については**サーバー エクスプ ローラー**ローカルの SharePoint サイトに接続するを参照してください。[参照 SharePoint 接続を使用してサーバー エクスプ ローラー](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)です。  
  
 拡張することができます、 **SharePoint 接続**ノードまたはカスタム ノード型を作成して、ノードの階層に追加することによって、既存のノードの拡張機能を作成します。  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>SharePoint 接続 ノードを拡張するためのタスク  
 既存のノードを拡張するを実装する Visual Studio 拡張機能を作成、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイスです。 ノードを拡張するときに、独自のショートカット メニュー項目またはカスタム プロパティなどのノードに機能を追加できます。 詳細については、次を参照してください。[する方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)です。  
  
 カスタム ノード型を作成するを実装する Visual Studio 拡張機能を作成、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>インターフェイスです。 表示されていない SharePoint サイトのコンポーネントを表示する場合は、カスタム ノードを作成する**サーバー エクスプ ローラー**既定です。 たとえば、**サーバー エクスプ ローラー**これを行うカスタム ノードを表示しない で、既定では、SharePoint サイトの Web パーツ ギャラリーを追加できますをしません。 詳細については、次を参照してください。[する方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)と[チュートリアル: サーバー エクスプ ローラー Web パーツの表示を拡張する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)です。  
  
## <a name="adding-custom-properties-to-nodes"></a>ノードにカスタム プロパティの追加  
 ノードを拡張またはカスタム ノード型を作成する場合は、ノードにカスタム プロパティを追加できます。 プロパティが表示されます、**プロパティ**ノードが選択されているときにウィンドウです。  
  
 ノードに追加できるカスタム プロパティの 2 つの種類があります。  
  
-   SharePoint サイトからの読み取り専用のデータのセットを表示するプロパティです。 データでは、ノードが表す SharePoint コンポーネントについて説明します。 これを行う方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: サーバー エクスプ ローラー Web パーツの表示を拡張する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)です。  
  
-   カスタムの読み取り/書き込みデータを表示するプロパティです。 これを行う方法を示すコード例を参照してください。[する方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)です。  
  
## <a name="getting-data-for-built-in-nodes"></a>組み込みのノードのデータの取得  
 すべての Visual Studio によって提供される組み込みのノードには、それらが表す SharePoint コンポーネントに関する一部のデータが含まれます。 たとえば、SharePoint サイトの一覧を表すノードは、タイトルと、一覧の既定のビューの URL など、リストに関する一部のデータを提供します。  
  
 このデータにアクセスするからのデータ オブジェクトを取得、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>興味のあるノードを表すオブジェクト。 データ オブジェクトの型は、ノードの種類によって異なります。  
  
 次のコード例では、一覧のノードのデータ オブジェクトを取得する方法を示します。 例のコンテキストでは、この例を参照してください[する方法: サーバー エクスプ ローラーで組み込みの SharePoint ノードのデータの取得](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)です。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 次の表は、組み込みのノードの種類ごとのデータ オブジェクトの種類を一覧表示します。  
  
|ノード型|データ オブジェクトの種類|  
|---------------|----------------------|  
|SharePoint サイト ノード|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|コンテンツの種類|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|特性|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|フィールド|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|リスト|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|一覧のテンプレート|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|リスト ビュー (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|ワークフローの関連付け|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|ワークフロー テンプレート|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロパティを参照してください[SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: サーバー エクスプ ローラー Web パーツ表示するための拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [方法: サーバー エクスプ ローラーで組み込みの SharePoint ノードのデータ取り出し](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [SharePoint ツール拡張機能とカスタム データの関連付け](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [サーバー エクスプ ローラーを使用して SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Visual Studio の SharePoint ツールの拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  