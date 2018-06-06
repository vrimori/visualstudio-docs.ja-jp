---
title: カスタム データを関連付ける SharePoint ツールの拡張機能 |Microsoft ドキュメント
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
ms.openlocfilehash: 051285d1a2b3fc1c32a813fbfd8aa778befa0545
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764876"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>SharePoint ツール拡張機能にカスタム データを関連付ける
  カスタム データは、SharePoint ツール拡張機能の特定のオブジェクトを追加することができます。 これは、機能は、後で、拡張機能の他のコードからアクセスする、拡張機能の 1 つの部分でデータがある場合に便利です。 保存し、データにアクセスするカスタム方法を実装するには、代わりには、拡張機能のオブジェクトとデータを関連付けるし、後で、同じオブジェクトからデータを取得します。  
  
 カスタム データ オブジェクトを追加するは、Visual Studio での特定の項目に関連するデータを保持する場合にも役立ちます。 Visual Studio で、そのため、拡張機能可能性があります機能をいくつかの異なる項目と 1 回では、SharePoint ツール拡張機能が読み込まれます (プロジェクトなどのプロジェクト項目、または**サーバー エクスプ ローラー**ノード) いつでもです。 特定の項目のみに関連するカスタムのデータを使用する場合は、項目を表すオブジェクトをデータを追加できます。  
  
 SharePoint ツール拡張機能内のオブジェクトにカスタム データを追加すると、データは保持されません。 データは、オブジェクトの有効期間中にのみ使用できます。 オブジェクトは、ガベージ コレクションによって回収されるが後のデータは失われます。  
  
 SharePoint プロジェクト システムの拡張で拡張が読み込まれるが引き続き発生する文字列データを保存することもできます。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
## <a name="objects-that-can-contain-custom-data"></a>カスタム データを含めることができるオブジェクト
 カスタム データを SharePoint ツールのオブジェクト モデルを実装する任意のオブジェクトを追加することができます、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>インターフェイスです。 このインターフェイスは、1 つのプロパティを定義<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>、カスタム データ オブジェクトのコレクションです。 次の種類を実装<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
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
  
## <a name="add-and-retrieve-custom-data"></a>追加およびカスタム データの取得
 SharePoint ツール拡張機能内のオブジェクトにカスタム データを追加するには、取得、 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 、データを追加し、使用するオブジェクトのプロパティ、<xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A>オブジェクトにデータを追加します。  
  
 SharePoint ツール拡張機能内のオブジェクトからカスタム データを取得、取得、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>オブジェクトと、次のメソッドのいずれか、使用のプロパティ。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>。 このメソッドが戻る**true**データ オブジェクトが存在する場合または**false**が存在しない場合。 このメソッドを使用すると、値の型または参照型のインスタンスを取得します。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>。 このメソッドは、データを返します。 セッションを終了する場合は、オブジェクトまたは**null**が存在しない場合。 このメソッドは、参照型のインスタンスを取得する場合のみ使用できます。  
  
 次のコード例では、特定のデータ オブジェクトは既にプロジェクト項目関連付けられているかどうかを判断します。 データ オブジェクトは、プロジェクト項目に関連付けられていないかどうかは、コードを追加するオブジェクト、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>プロジェクト項目のプロパティです。 例のコンテキストでは、この例を参照してください[する方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)です。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>関連項目
 [プログラミングに関する概念との SharePoint ツール拡張機能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [チュートリアル: 項目テンプレート、第 1 部にカスタム動作プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [チュートリアル: サーバー エクスプ ローラー Web パーツ表示するための拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [方法: プロパティをカスタムの SharePoint プロジェクト項目の種類に追加する](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 