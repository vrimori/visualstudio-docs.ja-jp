---
title: "方法: Deleter メソッドを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5e2ac47b315189dc2f0f7196db46aeb17ed08480
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-deleter-method"></a>方法: Deleter メソッドを追加する
  エンドユーザーがデータ レコードを追加することで SharePoint サイト上の外部リストから削除することができます、*デリーター*モデルへのメソッドです。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
### <a name="to-create-a-deleter-method"></a>削除子メソッドを作成するには  
  
1.  BDC デザイナーでは、エンティティを選択します。  
  
2.  メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、 **BDC メソッドの詳細**です。  
  
     **BDC メソッドの詳細**ウィンドウが開きます。 このウィンドウの詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)です。  
  
3.  **メソッドを追加**一覧で、選択**Deleter メソッドを作成する**です。  
  
     Visual Studio では、モデルに、次の要素を追加します。 これらの要素の表示で、 **BDC メソッドの詳細**ウィンドウです。  
  
    -   という名前のメソッド**削除**です。  
  
    -   メソッドの入力パラメーター。  
  
    -   パラメーターの型記述子。  
  
    -   メソッドのメソッドのインスタンス。  
  
     詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
4.  **ソリューション エクスプ ローラー**エンティティには、生成されたサービス コード ファイルのショートカット メニューを開きを選択し、**コードの表示**です。  
  
     エンティティ サービス コード ファイルでは、コード エディターで開きます。 エンティティ サービス コード ファイルの詳細については、次を参照してください。[ビジネス データ接続モデルを作成する](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
5.  レコードを削除する削除子メソッドにコードを追加します。 次の例は、SQL Server の AdventureWorks サンプル データベースを使用して、販売注文からの行アイテムを削除します。  
  
    > [!NOTE]  
    >  この例では、メソッドは、2 つの入力パラメーターを使用します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>参照  
 [ビジネス データ接続モデルの設計](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: Specificfinder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  