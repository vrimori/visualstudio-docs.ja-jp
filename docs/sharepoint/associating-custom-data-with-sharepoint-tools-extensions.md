---
title: ツールの拡張機能を SharePoint とカスタム データの関連付け |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b72e058a2ef025b0118dac8fd419e75d1ad53349
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327230"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>SharePoint ツール拡張機能とカスタム データを関連付ける
  カスタム データは、SharePoint ツール拡張機能の特定のオブジェクトを追加することができます。 これは、機能は、データが、拡張機能の他のコードから、後でアクセスする、拡張機能の 1 つの部分である場合に便利です。 データを格納し、アクセス、カスタマイズした方法を実装するには、代わりには、オブジェクトと、拡張機能で、データを関連付けるし、後で、同じオブジェクトからデータを取得します。  
  
 オブジェクトへのカスタム データの追加は、Visual Studio での特定の項目に関連するデータを保持する場合にも役立ちます。 Visual Studio で、そのため、拡張機能動作可能性があります複数の異なる項目を 1 回では、SharePoint ツール拡張機能が読み込まれる (など、プロジェクトのプロジェクト項目、または**サーバー エクスプ ローラー**ノード)、いつでもできます。 特定の項目のみに関連するカスタム データがあれば、その項目を表すオブジェクトをデータを追加できます。  
  
 SharePoint ツール拡張機能内のオブジェクトにカスタム データを追加すると、データは保持されません。 データは、オブジェクトの有効期間中にのみ使用できます。 オブジェクトはガベージ コレクションによって解放、後に、データが失われます。  
  
 SharePoint プロジェクト システムの拡張機能は、拡張機能が読み込まれるが解決しない文字列データを保存することもできます。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能内のデータ保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)します。  
  
## <a name="objects-that-can-contain-custom-data"></a>カスタム データを含むことのできるオブジェクト
 カスタム データを SharePoint ツール オブジェクト モデルを実装する任意のオブジェクトを追加することができます、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>インターフェイス。 このインターフェイスは、1 つのプロパティを定義します<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>、カスタム データ オブジェクトのコレクションです。 次の種類の実装<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>追加し、カスタム データの取得
 SharePoint ツール拡張機能内のオブジェクトには、カスタム データを追加するには、取得、 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 、データを追加し、使用するオブジェクトのプロパティ、<xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A>オブジェクトにデータを追加します。  
  
 SharePoint ツール拡張機能内のオブジェクトからのカスタム データを取得するには、取得、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>次のメソッドのいずれか、使用したオブジェクトのプロパティ。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>。 このメソッドが戻る**true**データ オブジェクトが存在する場合または**false**が存在しない場合。 このメソッドを使用すると、値の型または参照型のインスタンスを取得します。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>。 このメソッドは、データを返します。 セッションを終了する場合は、オブジェクトまたは**null**が存在しない場合。 このメソッドは、参照型のインスタンスを取得する場合のみ使用できます。  
  
 次のコード例では、特定のデータ オブジェクトがプロジェクト項目に関連付けが既にかどうかを判断します。 データ オブジェクトがプロジェクト項目に関連付けられていないかどうかは、オブジェクトを追加するコードを<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト項目のプロパティ。 例のコンテキストでは、この例を確認するには、次を参照してください。[方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)します。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>関連項目
 [プログラミングの概念と機能の SharePoint ツール拡張機能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [チュートリアル: 項目テンプレート、第 1 部でのカスタム動作プロジェクト項目の作成](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: web パーツを表示するサーバー エクスプ ローラーの拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 
