---
title: '方法: SharePoint Web パーツを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 708a1b1a0b64dbed5c02e6fcaf7da9e8892f5664
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-web-part"></a>方法: SharePoint Web パーツを作成する
  作成して追加することで web パーツのカスタマイズ、 **Web パーツ**を SharePoint プロジェクト項目および web パーツのまたは、デザイナーを使用して、コード ファイルを編集します。 詳細については、次を参照してください。[する方法: デザイナーを使用して、SharePoint Web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)です。  
  
### <a name="to-create-a-sharepoint-web-part"></a>SharePoint Web パーツを作成するには  
  
1.  SharePoint プロジェクトを作成するか開きます。  
  
     詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)です。  
  
2.  SharePoint プロジェクト ノードを選択**ソリューション エクスプ ローラー**を選択し**プロジェクト**、**新しい項目の追加**です。  
  
3.  **新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
4.  SharePoint テンプレートの一覧で選択**Web パーツ**です。  
  
5.  **名前**ボックス、web パーツの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     Web パーツの表示で**ソリューション エクスプ ローラー**です。 Web パーツに含まれるファイルの詳細については、次を参照してください。 [for SharePoint Web パーツを作成する](../sharepoint/creating-web-parts-for-sharepoint.md)です。  
  
6.  **ソリューション エクスプ ローラー**、先ほど作成した web パーツのコード ファイルを開きます。  
  
     たとえば、Web パーツの名前が WebPart1 の場合、WebPart1.vb (Visual Basic の場合) または WebPart1.cs (C# の場合) を開きます。  
  
7.  コード ファイルで、<xref:System.Web.UI.Control.CreateChildControls%2A> メソッドにコントロールを追加します。  
  
     例については、次を参照してください。[チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [方法: デザイナーを使用して、SharePoint Web パーツを作成します。](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [チュートリアル: SharePoint の Web パーツを作成します。](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  