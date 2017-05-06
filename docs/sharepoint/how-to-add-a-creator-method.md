---
title: "方法: Creator メソッドを追加する"
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
  - "BDC [Visual Studio での SharePoint 開発], 追加 (エンティティを)"
  - "BDC [Visual Studio での SharePoint 開発], 追加 (エンティティ インスタンスを)"
  - "BDC [Visual Studio での SharePoint 開発], Creator"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 追加 (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 追加 (エンティティ インスタンスを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], Creator"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 方法: Creator メソッドを追加する
  Creator メソッドを使用すると、エンティティのデータ ソースに新しいデータが追加されます。  ユーザーが、モデルに基づくリストのリボンの **\[新しいアイテム\]** ボタンをクリックすると、ビジネス データ接続 \(\(BDC\) サービスからこのメソッド。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
### Creator メソッドを追加するには  
  
1.  BDC デザイナーで、エンティティを選択します。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     **\[BDC メソッドの詳細\]** ウィンドウが表示されます。  このウィンドウの詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
3.  **\[メソッドの追加\]** の一覧で、**\[Creator メソッドの作成\]** をクリックします。  
  
     Visual Studio では、モデルに次の要素を追加して、これらの要素は **\[BDC メソッドの詳細\]** ウィンドウに表示されます。  
  
    -   **Create** というメソッド。  
  
    -   メソッドの入力パラメーター。  
  
    -   メソッドの戻り値パラメーター。  
  
    -   パラメーターの型記述子。  
  
    -   メソッドのメソッド インスタンス。  
  
     詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
4.  **\[ソリューション エクスプローラー\]** で、エンティティ用に生成された開き、**\[コードの表示\]** をクリックしますサービス コード ファイルのショートカット メニューを。  
  
     コード エディターで、エンティティ サービス コード ファイルが開きます。  エンティティ サービス コード ファイルの詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
5.  Creator メソッドには、データ ソースにデータを登録するコードを追加します。  次の例では、SQL Server の AdventureWorks サンプル データベースの連絡先を追加します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## 参照  
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  