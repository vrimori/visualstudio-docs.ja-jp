---
title: "方法: エンティティ間に関連付けを作成する"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 関連付け (外部コンテンツ タイプを)"
  - "BDC [Visual Studio での SharePoint 開発], 関連付け (エンティティ間の)"
  - "BDC [Visual Studio での SharePoint 開発], 作成 (関連付けを)"
  - "BDC [Visual Studio での SharePoint 開発], 関連付け (エンティティを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 関連付け (外部コンテンツ タイプを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 関連付け (エンティティ間の)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 作成 (関連付けを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 関連付け (エンティティを)"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法: エンティティ間に関連付けを作成する
  関連付けを作成することで、ビジネス データ接続 \(BDC\) モデルのエンティティ間の関連性を定義できます。  Visual Studio では、モデルの使用者に各関連付けに関する情報を提供するメソッドが生成されます。  これらのメソッドは、SharePoint Web パーツ、またはカスタム アプリケーションでユーザー インターフェイス \(UI\) データ リレーションシップを表示するために使用できます。  
  
 BDC デザイナーでは、外部キーに基づく関連付けと外部キーなしの関連付けという 2 種類の関連付けを作成できます。  詳細については、「[エンティティ間の関連付けの作成](../sharepoint/creating-an-association-between-entities.md)」を参照してください。  
  
### エンティティ間に関連付けを作成するには  
  
1.  **\[ツールボックス\]** の **\[BusinessDataConnectivity\]** タブで、**\[関連付け\]** 項目を選択します。  
  
2.  BDC デザイナーで、ソース エンティティを選択し、ターゲット エンティティを選択します。  
  
     **関連付けエディター** が表示されます。  
  
3.  外部キーに基づく関連付けを作成する場合、**\[外部キーの関連付けである\]** チェック ボックスをオンにします。  
  
    1.  **\[識別子のマッピング\]** テーブルの **\[ソース ID\]** の列で、**\[フィールド\]** の列の一致する各型記述子の横にある識別子を選択します。  
  
         たとえば、**\[ソース ID\]** 列で、`ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 型記述子と `ReadItem.salesOrder.SalesOrder.ContactID` 型記述子の横にある `ContactID` を選択します。  
  
4.  外部キーなしの関連付けを作成する場合、**\[外部キーの関連付けである\]** チェック ボックスをオフにします。  
  
5.  **\[OK\]** を選択します。  
  
6.  BDC デザイナーのソース エンティティとターゲット エンティティ間に、関連付けを示す行が表示されます。  
  
     Visual Studio では、ターゲット エンティティのサービス クラスとソース エンティティのサービス クラスに Association Navigator メソッドを追加しています。  Association Navigation のメソッドに関する詳細については、参照します [サポートされていない操作](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
7.  ソース エンティティの Association Navigator メソッドに、ターゲット エンティティのコレクションを返すコードを追加します。  
  
8.  ターゲット エンティティの Association Navigator メソッドに、関連するソース エンティティを返すコードを追加します。  
  
     Association Navigator メソッドの例については、「[エンティティ間の関連付けの作成](../sharepoint/creating-an-association-between-entities.md)」を参照してください。  
  
## 参照  
 [エンティティ間の関連付けの作成](../sharepoint/creating-an-association-between-entities.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法 : メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [チュートリアル: ビジネス データを使用した SharePoint での外部リストの作成](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  