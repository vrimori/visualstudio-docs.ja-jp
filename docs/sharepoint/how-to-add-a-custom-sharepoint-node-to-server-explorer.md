---
title: '方法: サーバー エクスプ ローラーにカスタム SharePoint ノードの追加 |Microsoft Docs'
ms.date: 02/02/2017
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
ms.openlocfilehash: bc648abd1d8981bd5c64782bd094e40d507b4142
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937664"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加します。
  カスタム ノードを追加することができます、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**します。 表示されていないその他の SharePoint コンポーネントを表示する場合に便利ですが**サーバー エクスプ ローラー**既定。 詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。  
  
 カスタム ノードを追加するには、まず新しいノードを定義するクラスを作成します。 次の既存のノードの子として、ノードを追加する拡張機能を作成します。  
  
### <a name="to-define-the-new-node"></a>新しいノードを定義するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> インターフェイスを実装するクラスを作成します。  
  
4.  クラスには、次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>属性コンス トラクターの型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>。 ノードの定義では、この属性は、新しいノードの文字列識別子を指定します。 形式を使用することをお勧めします*会社名*。 *。ノード名*のすべてのノードの一意の識別子であるかどうかを確認します。  
  
5.  実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>メソッドのメンバーを使用して、 *typeDefinition*パラメーターを新しいノードの動作を構成します。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>インターフェイス。  
  
     次のコード例では、新しいノードを定義する方法を示します。 この例では、プロジェクトにリソースとして埋め込ま CustomChildNodeIcon という名前のアイコンが含まれている前提としています。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>既存のノードの子として新しいノードを追加するには  
  
1.  ノードの定義と同じプロジェクトを実装するクラスを作成、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイス。  
  
2.  クラスに <xref:System.ComponentModel.Composition.ExportAttribute> 属性を追加します。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>属性コンス トラクターの型。  
  
3.  クラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 属性を追加します。 ノードの拡張機能では、この属性は、拡張するノードの型の文字列識別子を指定します。  
  
     Visual Studio によって提供される組み込みのノードの種類を指定するには、属性コンス トラクターに次の列挙値のいずれかを渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>:これらのサイト接続ノード (サイトの Url を表示するノード) を指定する値のサイト ノード、または他のすべての親ノードを使用して**サーバー エクスプ ローラー**します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>:これらの値を使用すると、リスト、フィールド、またはコンテンツの種類を表すノードなどの SharePoint サイト上の個々 のコンポーネントを表す組み込みのノードのいずれかを指定します。  
  
4.  実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>メソッドは、ハンドル、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>のイベント、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>パラメーター。  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>イベント ハンドラーでは、新しいノードの子ノードのコレクションを追加、<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A>イベント引数のパラメーターによって公開されるオブジェクト。  
  
     次のコード例は、SharePoint サイト ノードの子として新しいノードを追加する方法を示します**サーバー エクスプ ローラー**します。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>コード例全体
 次のコード例は、単純なノードを定義し、SharePoint サイト ノードの子として追加するコード全体を提供します。**サーバー エクスプ ローラー**します。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、プロジェクトにリソースとして埋め込ま CustomChildNodeIcon という名前のアイコンが含まれている前提としています。 この例では、次のアセンブリへの参照も必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 展開する、**サーバー エクスプ ローラー**拡張機能、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張します。](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [チュートリアル: Web パーツを表示するサーバー エクスプ ローラーを拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
