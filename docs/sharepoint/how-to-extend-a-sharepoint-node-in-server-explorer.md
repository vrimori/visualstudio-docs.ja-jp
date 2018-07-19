---
title: '方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1dee26ae729dedc2d38895ca84e430ffcbad875f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119799"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>方法: サーバー エクスプ ローラーでの SharePoint ノードを拡張
  下のノードを拡張することができます、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**します。 これは、既存のノードに新しい子ノード、ショートカット メニュー項目、またはプロパティを追加する場合に便利です。 詳細については、次を参照してください。[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>サーバー エクスプ ローラーでの SharePoint ノードを拡張するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装するクラスを作成します。  
  
4.  追加、<xref:System.ComponentModel.Composition.ExportAttribute>属性をクラス。 この属性により、Visual Studio を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>属性コンス トラクターの型。  
  
5.  追加、<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>属性をクラス。 この属性は、拡張するノードの型の文字列識別子を指定します。  
  
     Visual Studio によって提供される組み込みのノードの種類を指定するには、属性コンス トラクターに次の列挙値のいずれかを渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: ノード、またはその他のすべての親ノードでサイトのサイト接続ノード (サイトの Url を表示するノード) を指定するこれらの値使用**サーバー エクスプ ローラー**します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: リスト、フィールド、またはコンテンツの種類を表すノードなどの SharePoint サイト上の個々 のコンポーネントを表す組み込みのノードのいずれかを指定するのに、これらの値を使用します。  
  
6.  実装で、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>メソッドのメンバーを使用して、 *nodeType*パラメーター ノードに機能を追加します。 このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>で定義されたイベントへのアクセスを提供するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>インターフェイス。 たとえば、次のイベントを処理できます。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: ノードに新しい子ノードを追加するには、このイベントを処理します。 詳細については、次を参照してください。[方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: ノードにカスタムのショートカット メニュー項目を追加するには、このイベントを処理します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: ノードにカスタム プロパティを追加するには、このイベントを処理します。 プロパティが表示されます、**プロパティ**ノードが選択されている場合は、ウィンドウ。  
  
## <a name="example"></a>例  
 次のコード例では、2 つの異なる種類のノードの拡張機能を作成する方法を示します。  
  
-   SharePoint サイト ノードにコンテキスト メニュー項目を追加する拡張機能。 メニュー項目をクリックすると、クリックされたノードの名前が表示されます。  
  
-   という名前のカスタム プロパティを追加する拡張機能**ContosoExampleProperty**という名前のフィールドを表す各ノードに**本文**します。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 この拡張機能では、ノードに、編集可能な文字列プロパティを追加します。 SharePoint サーバーからの読み取り専用のデータを表示するカスタム プロパティを作成することもできます。 これを行う方法については、例では、次を参照してください。[チュートリアル: サーバー エクスプ ローラー web パーツを表示する拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)します。  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 この例では、次のアセンブリへの参照が必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>拡張機能をデプロイします。  
 展開する、**サーバー エクスプ ローラー**拡張機能、作成、[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]アセンブリおよびその他の拡張機能を配布するファイルの拡張機能 (VSIX) にパッケージ化します。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: サーバー エクスプ ローラーにカスタム SharePoint ノードを追加](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [チュートリアル: web パーツを表示するサーバー エクスプ ローラーの拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
