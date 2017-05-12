---
title: "方法: モデルにエンティティを追加する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 追加 (エンティティを)"
  - "BDC [Visual Studio での SharePoint 開発], エンティティ"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 追加 (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], エンティティ"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 方法: モデルにエンティティを追加する
  エンティティを作成するには、Business Data Connectivity \(BDC\) のデザイナーに Visual Studio **\[ツールボックス\]** からエンティティのコントロールを追加します。  
  
### モデルにエンティティを追加するには  
  
1.  BDC プロジェクトを作成するか、既存の BDC プロジェクトを開きます。  詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
2.  **\[ツールボックス\]** で、**\[BusinessDataCatalog\]** のグループからデザイナーに **\[エンティティ\]** のコントロールを追加します。  
  
     新しいエンティティがデザイナーに表示されます。  プロジェクトの BDC モデル ファイルの XML に、`<Entity>` 要素が追加されます。  エンティティの要素の属性の詳細については、参照します [エンティティ](http://go.microsoft.com/fwlink/?LinkId=169296)。  
  
3.  デザイナーのエンティティのショートカット メニューを開き、**\[追加\]** をクリックします、**\[識別子\]** をクリックします。  
  
     新しい識別子がエンティティに表示されます。  
  
    > [!NOTE]  
    >  エンティティの名前と識別子は **プロパティ** ウィンドウで変更できます。  
  
4.  クラス内のエンティティのフィールドを定義します。  新しいクラスを追加するか、オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) などのツールを使用して作成した既存のクラスを使用することができます。  次の例は、Contact という名前のエンティティ クラスを示しています。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## 参照  
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  