---
title: '方法: Creator メソッドの追加 |Microsoft Docs'
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
ms.openlocfilehash: 353d834ccd32376b53c875be356865711a4f89fd
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757241"
---
# <a name="how-to-add-a-creator-method"></a>方法: Creator メソッドを追加
  Creator メソッドでは、新しいデータがエンティティのデータ ソースを追加します。 クリックすると、ビジネス データ接続 (BDC) サービスはこのメソッドを呼び出して、**新しい項目の**のボタンでは、**リボン**モデルに基づいているリストの。 詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
### <a name="to-add-a-creator-method"></a>Creator メソッドを追加するには  
  
1.  **BDC デザイナー**エンティティを選択します。  
  
2.  メニュー バーで、**ビュー** > **その他の Windows** >**BDC メソッドの詳細**します。  
  
     **BDC メソッドの詳細**ウィンドウが開きます。 そのウィンドウの詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)します。  
  
3.  **メソッドを追加する**一覧で、選択**Creator メソッドの作成**です。  
  
     Visual Studio は、モデルに、次の要素を追加し、これらの要素、 **BDC メソッドの詳細**ウィンドウ。  
  
    -   という名前のメソッド**作成**です。  
  
    -   メソッドの入力パラメーター。  
  
    -   メソッドの戻り値のパラメーター。  
  
    -   パラメーターの記述子を入力します。  
  
    -   メソッドのメソッドのインスタンス。  
  
     詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
4.  **ソリューション エクスプ ローラー**エンティティの場合に生成されたサービスのコード ファイルのショートカット メニューを開き、選択し、**コードの表示**します。  
  
     エンティティ サービス コード ファイルがコード エディターで開きます。 詳細については、エンティティ サービス コード ファイルは、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
5.  データ ソースにデータを追加する Creator メソッドにコードを追加します。 次の例では、SQL Server の AdventureWorks サンプル データベースへ、連絡先を追加します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドの追加](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスの定義](../sharepoint/how-to-define-a-method-instance.md)  
  
  
