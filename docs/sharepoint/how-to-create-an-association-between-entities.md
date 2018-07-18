---
title: '方法: エンティティ間のアソシエーションの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51527092332f1fa82019f1abf9251a8b44aedf06
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119462"
---
# <a name="how-to-create-an-association-between-entities"></a>方法: エンティティ間のアソシエーションの作成
  関連付けを作成して、ビジネス データ接続 (BDC) モデルのエンティティ間のリレーションシップを定義することができます。 Visual Studio では、各関連付けについての情報をモデルのコンシューマーに提供するメソッドを生成します。 これらのメソッドは、SharePoint web パーツ、リスト、またはユーザー インターフェイス (UI) でデータ間の関係を表示するカスタム アプリケーションで使用できます。  
  
 2 つの種類のアソシエーションを作成するには、BDC デザイナーに: 外部キーに基づくアソシエーションおよび外部キーを使用しないアソシエーション。 詳細については、次を参照してください。[エンティティ間のアソシエーションを作成する](../sharepoint/creating-an-association-between-entities.md)します。  
  
### <a name="to-create-an-association-between-entities"></a>エンティティ間のアソシエーションを作成するには  
  
1.  **BusinessDataConnectivity**のタブ、**ツールボックス**、選択、**アソシエーション**項目。  
  
2.  BDC デザイナーで、ソース エンティティを選択し、転送先エンティティをします。  
  
     **関連付けエディター**が表示されます。  
  
3.  外部キーに基づく関連付けを作成する場合は、選択、**外部キーの関連付け**チェック ボックスをオンします。  
  
    1.  **ソース ID**の列、**識別子のマッピング**テーブルに表示される各一致する型記述子の横にある識別子を選択、**フィールド**列。  
  
         などで、**ソース ID**列で、`ContactID`横に、`ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID`記述子を入力し、`ReadItem.salesOrder.SalesOrder.ContactID`記述子を入力します。  
  
4.  外部キーなしの関連付けを作成する場合は、オフ、**外部キーの関連付け**チェック ボックスをオンします。  
  
5.  **[OK]** を選択します。  
  
6.  BDC デザイナーでは、ソース エンティティと転送先エンティティの間の関連付けを表す線が表示されます。  
  
     Visual Studio では、転送先エンティティのサービス クラスとソース エンティティのサービス クラスにメソッドをアソシエーション ナビゲーターを追加します。 アソシエーションのナビゲーション方法の詳細については、次を参照してください。[サポートされている操作](http://go.microsoft.com/fwlink/?LinkId=169286)します。  
  
7.  ソース エンティティの関連付けのナビゲーター メソッドでは、移行先のエンティティのコレクションを返すコードを追加します。  
  
8.  転送先エンティティの関連付けのナビゲーター メソッドでは、関連するソース エンティティを返すコードを追加します。  
  
     ナビゲーターの関連付けの方法の例については、次を参照してください。[エンティティ間のアソシエーションを作成する](../sharepoint/creating-an-association-between-entities.md)します。  
  
## <a name="see-also"></a>関連項目
 [エンティティ間のアソシエーションを作成します。](../sharepoint/creating-an-association-between-entities.md)   
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドの追加](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスの定義](../sharepoint/how-to-define-a-method-instance.md)   
 [方法: パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [チュートリアル: sharepoint ビジネス データを使用して外部リストを作成します。](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
