---
title: "方法: Updater メソッドを追加する"
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
  - "BDC [Visual Studio での SharePoint 開発], Updater"
  - "BDC [Visual Studio での SharePoint 開発], 更新 (データを)"
  - "BDC [Visual Studio での SharePoint 開発], 更新 (エンティティ インスタンスを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], Updater"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 更新 (データを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 更新 (エンティティ インスタンスを)"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 方法: Updater メソッドを追加する
  *Updater* メソッドを作成することで、SharePoint 外部リストのビジネス データを更新できるようになります。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
### Updater メソッドを作成するには  
  
1.  BDC デザイナーで、エンティティを選択します。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     \[BDC メソッドの詳細\] ウィンドウが表示されます。  このウィンドウの詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
3.  **\[メソッドの追加\]** の一覧で、**\[Updater メソッドの作成\]** をクリックします。  
  
     次の要素がモデルに追加されます。  これらの要素は \[BDC メソッドの詳細\] ウィンドウに表示されます。  
  
    -   **\[更新\]** というメソッド。  
  
    -   メソッドの入力パラメーター。  
  
    -   パラメーターの型記述子。  Visual Studio では、既定により、Finder メソッドに対して定義したエンティティ型記述子 \(例: Contact\) が使用されます。  
  
    -   メソッドのメソッド インスタンス。  
  
     詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
    > [!NOTE]  
    >  エンティティ型の識別子が自動的に生成しないデータベース テーブルのフィールドを表している **\[True\]** に **\[Pre\-Updater フィールド\]** のプロパティを設定します。  
  
4.  **\[ソリューション エクスプローラー\]** で、エンティティ用に生成された開き、**\[コードの表示\]** をクリックしますサービス コード ファイルのショートカット メニューを。  
  
     コード エディターで、エンティティ サービス コード ファイルが開きます。  このファイルの詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
5.  データを更新する場合は、Update メソッドにコードを追加します。  次の例では、SQL Server の AdventureWorks サンプル データベースの連絡先に関する情報を更新します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## 参照  
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  