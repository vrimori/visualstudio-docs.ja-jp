---
title: サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c10906f21a6379d0f1797fa7986e33a401de32f5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876136"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。
  使用して Visual Studio で、開発用コンピューターでローカルの SharePoint サイトに接続できる、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウ。 このノードは、階層ツリー ビューで、ローカルの SharePoint サイトのコンポーネントの多くを表示します。 たとえば、ローカル サイトでは、リスト、ドキュメント ライブラリ、およびコンテンツの種類を表示できます。 使用しての詳細については**サーバー エクスプ ローラー**ローカル SharePoint サイトに接続するを参照してください。[参照 SharePoint 接続のサーバー エクスプ ローラーを使用して](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)します。  
  
 拡張することができます、 **SharePoint 接続**ノードまたはノードの階層に追加することをカスタム ノード型を作成して既存のノードの拡張機能を作成します。  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>SharePoint 接続 ノードを拡張するためのタスク
 既存のノードを拡張するには、実装する Visual Studio 拡張機能を作成、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイス。 ノードを拡張するときは、独自のショートカット メニュー項目またはカスタム プロパティなどのノードに機能を追加できます。 詳細については、「[方法 :サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)します。  
  
 カスタム ノード型を作成するには、実装する Visual Studio 拡張機能を作成、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>インターフェイス。 表示されていない SharePoint サイトのコンポーネントを表示するには、カスタム ノードを作成**サーバー エクスプ ローラー**既定。 たとえば、**サーバー エクスプ ローラー**これを行うカスタム ノードを表示しない が既定での SharePoint サイトの Web パーツ ギャラリーを追加できますにしません。 詳細については、「[方法 :サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)と[チュートリアル。Web パーツを表示するサーバー エクスプ ローラーを拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)します。  
  
## <a name="add-custom-properties-to-nodes"></a>カスタム プロパティのノードを追加します。
 ノードを拡張またはカスタム ノード型を作成するときに、ノードにカスタム プロパティを追加できます。 プロパティが表示されます、**プロパティ**ノードが選択されている場合は、ウィンドウ。  
  
 2 種類のノードに追加できるカスタム プロパティがあります。  
  
-   SharePoint サイトからの読み取り専用のデータのセットを表示するプロパティ。 データには、ノードが表す SharePoint コンポーネントについて説明します。 これを行う方法について説明するチュートリアルでは、次を参照してください。[チュートリアル。Web パーツを表示するサーバー エクスプ ローラーを拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)します。  
  
-   カスタムの読み取り/書き込みデータを表示するプロパティです。 これを行う方法を示すコード例を参照してください。[方法。サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)します。  
  
## <a name="get-data-for-built-in-nodes"></a>組み込みのノードのデータを取得します。
 すべての Visual Studio によって提供される組み込みのノードには、それが表す SharePoint コンポーネントについてのデータが含まれます。 たとえば、SharePoint サイトのリストを表すノードは、タイトル、および一覧については、既定のビューの URL など、一覧の一部のデータを提供します。  
  
 このデータにアクセスするからのデータ オブジェクトを取得、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>興味のあるノードを表すオブジェクト。 データ オブジェクトの型は、ノードの種類によって異なります。  
  
 次のコード例では、一覧のノードのデータ オブジェクトを取得する方法を示します。 例のコンテキストでは、この例を確認するには、次を参照してください。[方法。サーバー エクスプ ローラーで、組み込みの SharePoint ノードのデータを取得](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)します。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 次の表では、組み込みのノードの種類ごとのデータ オブジェクトの種類を示します。  
  
|ノード型|データ オブジェクトの種類|  
|---------------|----------------------|  
|SharePoint サイト ノード|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|コンテンツ タイプ|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|機能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|フィールド|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|リスト|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|リスト テンプレート|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|リスト ビュー (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|ワークフローの関連付け|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|ワークフロー テンプレート|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 使用しての詳細については、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロパティを参照してください[ツールの拡張機能を SharePoint でカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)します。  
  
## <a name="see-also"></a>関連項目
 [チュートリアル: Web パーツを表示するサーバー エクスプ ローラーを拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張します。](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加します。](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [方法: サーバー エクスプ ローラーで、組み込みの SharePoint ノードのデータを取得します。](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [サーバー エクスプ ローラーを使用した SharePoint 接続を参照します。](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Visual Studio の SharePoint ツールを拡張します。](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
