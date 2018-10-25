---
title: '方法: Updater メソッドの追加 |Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4d50180173673b4999c18b8980c682d79637bd3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951419"
---
# <a name="how-to-add-an-updater-method"></a>方法: Updater メソッドの追加
  ユーザーを作成して SharePoint の外部リストのビジネス データを更新できるように、 *Updater*メソッド。 詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
### <a name="to-create-an-updater-method"></a>Updater メソッドを作成するには  
  
1. BDC デザイナーでは、エンティティを選択します。  
  
2. メニュー バーで、**ビュー** > **その他の Windows** > **BDC メソッドの詳細**します。  
  
    BDC メソッドの詳細ウィンドウが開きます。 このウィンドウの詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)します。  
  
3. **メソッドを追加する**一覧で、選択**Updater メソッドの作成**です。  
  
    Visual Studio では、モデルに、次の要素を追加します。 これらの要素は、BDC メソッドの詳細ウィンドウに表示されます。  
  
   - という名前のメソッド**Update**します。  
  
   - メソッドの入力パラメーター。  
  
   - パラメーターの型記述子。 既定で、Visual Studio は Finder メソッドの定義したエンティティ型記述子を使用して (例: にお問い合わせください)。  
  
   - メソッドのメソッドのインスタンス。  
  
     詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
   > [!NOTE]  
   >  エンティティ型の識別子が自動的に生成されるデータベース テーブル内のフィールドを表している場合は、設定、 **Pre-updater フィールド**プロパティを**True**します。  
  
4. **ソリューション エクスプ ローラー**エンティティの場合に生成されたサービスのコード ファイルのショートカット メニューを開き、選択し、**コードの表示**します。  
  
    エンティティ サービス コード ファイルが開き、**コード エディター**します。 そのファイルに関する詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
5. データを更新する Update メソッドにコードを追加します。 次の例では、SQL Server については、AdventureWorks サンプル データベース内の連絡先の情報を更新します。  
  
   > [!NOTE]  
   >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Updater メソッドの追加](../sharepoint/how-to-add-an-updater-method.md)   
 [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスの定義](../sharepoint/how-to-define-a-method-instance.md)  
  
 
