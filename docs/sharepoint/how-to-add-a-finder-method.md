---
title: "方法: Finder メソッドを追加する | Microsoft Docs"
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
  - "BDC [Visual Studio での SharePoint 開発], Finder メソッド"
  - "BDC [Visual Studio での SharePoint 開発], 取得 (エンティティを)"
  - "BDC [Visual Studio での SharePoint 開発], 返す (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], Finder メソッド"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 取得 (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 返す (エンティティを)"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 方法: Finder メソッドを追加する
  ビジネス データ接続サービスが Web パーツのエンティティのリストまたはリストを表示できるようにするには、*Finder* メソッドを作成する必要があります。  Finder メソッドは、エンティティ インスタンスのコレクションを返す特殊なメソッドです。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
### Finder メソッドを作成するには  
  
1.  BDC デザイナーで、エンティティを選択します。  
  
     詳細については、「[方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)」を参照してください。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     **\[BDC メソッドの詳細\]** ウィンドウが表示されます。  **\[BDC メソッドの詳細\]** ウィンドウの詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
3.  **\[メソッドの追加\]** の一覧で、**\[Finder メソッドの作成\]** をクリックします。  
  
     メソッド、戻り値パラメーター、および型記述子が追加されます。  
  
4.  エンティティ コレクション型記述子として型記述子を構成します。  エンティティ コレクション型記述子の作成方法の詳細については、「[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)」を参照してください。  
  
    > [!NOTE]  
    >  SpecificFinder メソッドをエンティティに追加した場合、この手順を実行する必要はありません。  Visual Studio では、SpecificFinder メソッドで定義した型記述子が使用されます。  
  
5.  **\[ソリューション エクスプローラー\]** で、エンティティ用に生成された開き、**\[コードの表示\]** をクリックしますサービス コード ファイルのショートカット メニューを。  サービス コード ファイルの詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
6.  Finder メソッドにコードを追加します。  このコードは次のタスクを実行します。  
  
    -   データ ソースからデータを取得します。  
  
    -   エンティティの一覧を BDC サービスに返します。  
  
     次の例では、SQL Server の AdventureWorks サンプル データベースのデータを使用して、`Contact` エンティティのコレクションを返します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## 参照  
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  