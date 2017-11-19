---
title: "方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張 |Microsoft ドキュメント"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98dd11e74053bde9ad1ec2e23f4f663dfa7d1e1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>方法: サーバー エクスプローラーの SharePoint ノードを拡張する
  下にノードを拡張することができます、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**です。 これは、既存のノードに新しい子ノード、ショートカット メニュー項目、またはプロパティを追加する場合に便利です。 詳細については、次を参照してください。[サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張する](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)です。  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>サーバー エクスプ ローラーでの SharePoint ノードを拡張するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装するクラスを作成します。  
  
4.  追加、<xref:System.ComponentModel.Composition.ExportAttribute>属性クラスにします。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>属性コンス トラクターの型。  
  
5.  追加、<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>属性クラスにします。 この属性は、拡張するノードの型の文字列識別子を指定します。  
  
     Visual Studio によって提供される組み込みのノード型を指定するには、次の列挙値のいずれかを属性コンス トラクターに渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: これらの値を、サイト接続ノード (サイトの Url を表示するノード) を指定するサイトのノード、またはその他のすべての親ノードで使用**サーバー エクスプ ローラー**です。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: リスト、フィールド、またはコンテンツの種類を表すノードなど、SharePoint サイト上の個々 のコンポーネントを表す組み込みノードのいずれかを指定するのにこれらの値を使用します。  
  
6.  実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>メソッドを使用するメンバーの*nodeType*パラメーター ノードに機能を追加します。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>インターフェイスです。 たとえば、次のイベントを処理できます。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: ノードに新しい子ノードを追加するには、このイベントを処理します。 詳細については、次を参照してください。[する方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)です。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: ノードにカスタムのショートカット メニュー項目を追加するには、このイベントを処理します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: ノードにカスタム プロパティを追加するには、このイベントを処理します。 プロパティが表示されます、**プロパティ**ノードが選択されているときにウィンドウです。  
  
## <a name="example"></a>例  
 次のコード例では、次の 2 つのさまざまな種類のノードの拡張機能を作成する方法を示します。  
  
-   SharePoint サイトのノードにコンテキスト メニュー項目を追加する拡張機能。 メニュー項目をクリックすると、クリックされたノードの名前が表示されます。  
  
-   という名前のカスタム プロパティを追加する拡張**ContosoExampleProperty**という名前のフィールドを表すの各ノードに**本文**です。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 この拡張機能は、ノードを編集可能な文字列プロパティを追加します。 SharePoint サーバーからの読み取り専用のデータを表示するカスタム プロパティを作成することもできます。 これを行う方法を示す例を参照してください[チュートリアル: サーバー エクスプ ローラー Web パーツの表示を拡張する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>拡張機能の配置  
 展開する、**サーバー エクスプ ローラー**拡張機能、作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [チュートリアル: サーバー エクスプ ローラー Web パーツ表示するための拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [カスタム データの SharePoint ツールの拡張機能への関連付け](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  