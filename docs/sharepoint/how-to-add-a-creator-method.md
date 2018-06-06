---
title: '方法: Creator メソッドを追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd566eacba7f94cfe7617e9396440c90dc32f51e
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767137"
---
# <a name="how-to-add-a-creator-method"></a>方法: Creator メソッドを追加
  Creator メソッドは、エンティティのデータ ソースに新しいデータを追加します。 クリックすると、ビジネス データ接続 (BDC) サービスがこのメソッドを呼び出して、**新しい項目の**ボタンをクリックして、**リボン**モデルに基づいているリストのです。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
### <a name="to-add-a-creator-method"></a>Creator メソッドを追加するには  
  
1.  **BDC デザイナー**エンティティを選択します。  
  
2.  メニュー バーで、次のように選択します。**ビュー** > **その他のウィンドウ** >**BDC メソッドの詳細**です。  
  
     **BDC メソッドの詳細**ウィンドウが開きます。 そのウィンドウの詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)です。  
  
3.  **メソッドを追加**一覧で、選択**Creator メソッドの作成**です。  
  
     Visual Studio は、モデルを次の要素を追加し、これらの要素に表示、 **BDC メソッドの詳細**ウィンドウです。  
  
    -   という名前のメソッド**作成**です。  
  
    -   メソッドの入力パラメーター。  
  
    -   メソッドの戻り値のパラメーターです。  
  
    -   パラメーターの記述子を入力します。  
  
    -   メソッドのメソッドのインスタンス。  
  
     詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
4.  **ソリューション エクスプ ローラー**エンティティには、生成されたサービス コード ファイルのショートカット メニューを開きを選択し、**コードの表示**です。  
  
     エンティティ サービス コード ファイルでは、コード エディターで開きます。 エンティティ サービス コード ファイルの詳細については、次を参照してください。[ビジネス データ接続モデルを作成する](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
5.  データ ソースにデータを追加する Creator メソッドにコードを追加します。 次の例では、SQL Server の AdventureWorks サンプル データベースに連絡先を追加します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルの設計](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: Specificfinder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)  
  
  