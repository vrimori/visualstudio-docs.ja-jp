---
title: "方法: SpecificFinder メソッドを追加する | Microsoft Docs"
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
  - "BDC [Visual Studio での SharePoint 開発], 取得 (エンティティを)"
  - "BDC [Visual Studio での SharePoint 開発], 返す (エンティティを)"
  - "BDC [Visual Studio での SharePoint 開発], SpecificFinder"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 取得 (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 返す (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], SpecificFinder"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 方法: SpecificFinder メソッドを追加する
  *SpecificFinder* メソッドを作成して、単一のエンティティ インスタンスを返すことができます。  Business Data Connectivity \(BDC\) サービスは、ユーザーがビジネス データ Web パーツまたは外部リストにエンティティを選択すると、特定の Finder メソッドを実行します。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
### SpecificFinder メソッドを作成するには  
  
1.  BDC デザイナーで、エンティティを選択します。  
  
     Visual Studio の BDC デザイナーにエンティティを追加する方法の詳細については、「[方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)」を参照してください。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     **\[BDC メソッドの詳細\]** ウィンドウが表示されます。  このウィンドウの詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
3.  **\[メソッドの追加\]** の一覧で、**\[SpecificFinder メソッドの作成\]** をクリックします。  
  
     次の要素がモデルに追加されます。  これらの要素は **\[BDC メソッドの詳細\]** ウィンドウに表示されます。  
  
    -   メソッド。  
  
    -   メソッドの入力パラメーター。  
  
    -   メソッドの戻り値パラメーター。  
  
    -   各パラメーターの型記述子。  
  
    -   メソッドのメソッド インスタンス。  
  
     詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
4.  Visual Studio の**プロパティ** ウィンドウを開きます。  
  
5.  戻り値パラメーターの型記述子をエンティティ型記述子として構成します。  エンティティ型記述子の作成方法の詳細については、「[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)」を参照してください。  
  
    > [!NOTE]  
    >  Finder メソッドをエンティティに追加した場合、この手順を実行する必要はありません。  Visual Studio では、Finder メソッドで定義した型記述子が使用されます。  
  
    > [!NOTE]  
    >  エンティティ型の識別子フィールドが自動的に生成されるデータベース テーブルのフィールドを表している **\[True\]**、識別子フィールドの **\[読み取り専用\]** のプロパティを設定します。  
  
6.  **\[メソッドの詳細\]** ウィンドウで、メソッドのメソッド インスタンスを選択します。  
  
7.  **プロパティ ウィンドウ**で、**"戻り値パラメーター名"** プロパティをメソッドの戻り値パラメーターの名前に設定します。  メソッド インスタンスのプロパティに関する詳細については、参照します [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
8.  **\[ソリューション エクスプローラー\]** で、エンティティ用に生成された開き、**\[コードの表示\]** をクリックしますサービス コード ファイルのショートカット メニューを。  
  
     コード エディターで、エンティティ サービス コード ファイルが開きます。  エンティティ サービス コード ファイルの詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
9. SpecificFinder メソッドにコードを追加します。  このコードは次のタスクを実行します。  
  
    -   データ ソースからレコードを取得します。  
  
    -   エンティティを BDC サービスに返します。  
  
     次の例では、SQL Server の AdventureWorks サンプル データベースの連絡先を返します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## 参照  
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  