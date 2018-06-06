---
title: '方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 878a2c76bbc57983791b65b73c8e0580dbfa3cfd
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767492"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加
  カスタムのノードを追加することができます、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**です。 これが役に表示されていないその他の SharePoint コンポーネントを表示するときに**サーバー エクスプ ローラー**既定です。 詳細については、次を参照してください。[サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張する](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)です。  
  
 カスタム ノードを追加するには、まず新しいノードを定義するクラスを作成します。 次に、ノードを既存のノードの子として追加する拡張機能を作成します。  
  
### <a name="to-define-the-new-node"></a>新しいノードを定義するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>属性コンス トラクターの型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>。 ノードの定義では、この属性は、新しいノードの文字列識別子を指定します。 形式を使用することをお勧め*会社名*.*ノード名*のすべてのノードの一意の識別子であるかどうかを確認します。  
  
5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>メソッドを使用するメンバーの*typeDefinition*パラメーターを新しいノードの動作を構成します。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>インターフェイスです。  
  
     次のコード例では、新しいノードを定義する方法を示します。 この例では、プロジェクトにリソースとして埋め込ま CustomChildNodeIcon をという名前のアイコンが含まれていると仮定します。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>既存のノードの子として新しいノードを追加するには  
  
1.  プロジェクト内で、同じノードの定義として、作成を実装するクラス、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイスです。  
  
2.  追加、<xref:System.ComponentModel.Composition.ExportAttribute>属性クラスにします。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>属性コンス トラクターの型。  
  
3.  追加、<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>属性クラスにします。 ノードの拡張機能では、この属性は、拡張するノードの型の文字列識別子を指定します。  
  
     Visual Studio によって提供される組み込みのノード型を指定するには、次の列挙値のいずれかを属性コンス トラクターに渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: これらの値を、サイト接続ノード (サイトの Url を表示するノード) を指定するサイトのノード、またはその他のすべての親ノードで使用**サーバー エクスプ ローラー**です。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: リスト、フィールド、またはコンテンツの種類を表すノードなど、SharePoint サイト上の個々 のコンポーネントを表す組み込みノードのいずれかを指定するのにこれらの値を使用します。  
  
4.  実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>メソッドは、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>のイベント、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>パラメーター。  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 、イベント ハンドラーの子ノードのコレクションに新しいノードを追加、<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A>イベントの引数パラメーターによって公開されるオブジェクト。  
  
     次のコード例は、SharePoint サイト内のノードの子として新しいノードを追加する方法を示します**サーバー エクスプ ローラー**です。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>コード例全体
 次のコード例は、単純なノードを定義し、SharePoint サイト内のノードの子として追加する完全なコードを提供**サーバー エクスプ ローラー**です。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、プロジェクトにリソースとして埋め込ま CustomChildNodeIcon をという名前のアイコンが含まれていると仮定します。 この例では、次のアセンブリへの参照も必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 展開する、**サーバー エクスプ ローラー**拡張機能、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [チュートリアル: サーバー エクスプローラーを拡張して Web パーツを表示する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  
