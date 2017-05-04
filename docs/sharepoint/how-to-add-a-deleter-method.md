---
title: "方法: Deleter メソッドを追加する | Microsoft Docs"
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
  - "BDC [Visual Studio での SharePoint 開発], Deleter"
  - "BDC [Visual Studio での SharePoint 開発], 削除 (データを)"
  - "BDC [Visual Studio での SharePoint 開発], 削除 (エンティティ インスタンスを)"
  - "BDC [Visual Studio での SharePoint 開発], 削除 (データを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], Deleter"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 削除 (データを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 削除 (エンティティ インスタンスを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 削除 (データを)"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法: Deleter メソッドを追加する
  エンド ユーザーが SharePoint サイト上の外部リストからデータ レコードを削除できるようにするには、*Deleter* メソッドをモデルに追加します。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
### Deleter メソッドを作成するには  
  
1.  BDC デザイナーで、エンティティを選択します。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     **\[BDC メソッドの詳細\]** ウィンドウが表示されます。  このウィンドウの詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
3.  **\[メソッドの追加\]** の一覧で、**\[削除するメソッドを作成します。\]** をクリックします。  
  
     次の要素がモデルに追加されます。  これらの要素は **\[BDC メソッドの詳細\]** ウィンドウに表示されます。  
  
    -   **Delete** というメソッド。  
  
    -   メソッドの入力パラメーター。  
  
    -   パラメーターの型記述子。  
  
    -   メソッドのメソッド インスタンス。  
  
     詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
4.  **\[ソリューション エクスプローラー\]** で、エンティティ用に生成された開き、**\[コードの表示\]** をクリックしますサービス コード ファイルのショートカット メニューを。  
  
     コード エディターで、エンティティ サービス コード ファイルが開きます。  エンティティ サービス コード ファイルの詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
5.  Deleter メソッドにコードを追加して、レコードを削除します。  次の例では、SQL Server の AdventureWorks サンプル データベースを使用して、販売注文から品目を削除します。  
  
    > [!NOTE]  
    >  この例のメソッドでは、2 つの入力パラメーターを使用しています。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## 参照  
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  