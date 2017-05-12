---
title: "方法: SharePoint Web パーツを作成する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Web パーツ [Visual Studio での SharePoint 開発], 追加"
  - "Web パーツ [Visual Studio での SharePoint 開発], 作成"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 方法: SharePoint Web パーツを作成する
  Web パーツを作成したりカスタマイズしたりするには、SharePoint プロジェクトに **Web パーツ**項目を追加して Web パーツのコード ファイルを編集する方法と、デザイナーを使用する方法があります。  詳細については、「[方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)」を参照してください。  
  
### SharePoint Web パーツを作成するには  
  
1.  SharePoint プロジェクトを作成するか開きます。  
  
     詳細については、「[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で SharePoint プロジェクト ノードを選択し、**\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[SharePoint\]** ノードを展開し、**\[2010\]** ノードを選択します。  
  
4.  SharePoint テンプレートの一覧で、**\[Web パーツ\]** を選択します。  
  
5.  **\[名前\]** ボックスに Web パーツの名前を入力し、**\[追加\]** をクリックします。  
  
     **ソリューション エクスプローラー**に Web パーツが表示されます。  Web パーツに含まれるファイルの詳細については、「[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)」を参照してください。  
  
6.  **ソリューション エクスプローラー**で、作成した Web パーツのコード ファイルを開きます。  
  
     たとえば、Web パーツの名前が WebPart1 の場合、WebPart1.vb \(Visual Basic の場合\) または WebPart1.cs \(C\# の場合\) を開きます。  
  
7.  コード ファイルで、<xref:System.Web.UI.Control.CreateChildControls%2A> メソッドにコントロールを追加します。  
  
     例については、「[チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)」を参照してください。  
  
## 参照  
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  