---
title: "方法: SharePoint Web パーツを作成 |Microsoft ドキュメント"
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
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847124dc9a7e4cd80993df5b50c5d3d3b752f228
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
  
  