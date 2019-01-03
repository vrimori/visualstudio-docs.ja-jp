---
title: '方法: SharePoint Web パーツの作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 43d776a4031cabfd027c96105f3e71a93ea1c07f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858424"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>方法: SharePoint web パーツを作成します。
  作成して web パーツを追加することでカスタマイズを**Web パーツ**を SharePoint プロジェクト項目し、web パーツまたはデザイナーを使用してコード ファイルを編集します。 詳細については、「[方法 :デザイナーを使用して、SharePoint web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)します。  
  
### <a name="to-create-a-sharepoint-web-part"></a>SharePoint web パーツを作成するには
  
1.  SharePoint プロジェクトを作成するか開きます。  
  
     詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。  
  
2.  SharePoint プロジェクト ノードを選択**ソリューション エクスプ ローラー**選び、**プロジェクト** > **新しい項目の追加**します。  
  
3.  **新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
4.  SharePoint テンプレートの一覧で選択**Web パーツ**します。  
  
5.  **名前**ボックス、web パーツの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     Web パーツの表示で**ソリューション エクスプ ローラー**します。 Web パーツを含むファイルの詳細については、次を参照してください。[の SharePoint web パーツを作成](../sharepoint/creating-web-parts-for-sharepoint.md)です。  
  
6.  **ソリューション エクスプ ローラー**、先ほど作成した web パーツのコード ファイルを開きます。  
  
     たとえば、web パーツの名前は*WebPart1*、オープン*WebPart1.vb* (Visual Basic) でまたは*webpart1.cs 場合*(で C# の場合)。  
  
7.  コード ファイルで、<xref:System.Web.UI.Control.CreateChildControls%2A> メソッドにコントロールを追加します。  
  
     例については、次を参照してください。[チュートリアル。For SharePoint web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)します。  
  
## <a name="see-also"></a>関連項目
 [For SharePoint の web パーツを作成します。](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [方法: デザイナーを使用して、SharePoint web パーツを作成します。](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [チュートリアル: For SharePoint の web パーツを作成します。](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [チュートリアル: デザイナーを使用して、SharePoint の web パーツを作成します。](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
