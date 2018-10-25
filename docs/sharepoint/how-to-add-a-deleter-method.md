---
title: '方法: Deleter メソッドの追加 |Microsoft Docs'
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0bc47da90356149e3fe2e1d1b888bf5ac6a877e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842678"
---
# <a name="how-to-add-a-deleter-method"></a>方法: Deleter メソッドを追加
  SharePoint サイト上の外部リストから、モデルに Deleter メソッドを追加してデータ レコードを削除するには、エンドユーザーを有効にすることができます。 詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
### <a name="to-create-a-deleter-method"></a>Deleter メソッドを作成するには  
  
1. **BDC デザイナー**エンティティを選択します。  
  
2. メニュー バーで、**ビュー** > **その他の Windows** > **BDC メソッドの詳細**します。  
  
    **BDC メソッドの詳細**ウィンドウが開きます。 このウィンドウの詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)します。  
  
3. **メソッドを追加する**一覧で、選択**Deleter メソッドを作成する**します。  
  
    Visual Studio では、モデルに、次の要素を追加します。 これらの要素、 **BDC メソッドの詳細**ウィンドウ。  
  
   - という名前のメソッド**削除**します。  
  
   - メソッドの入力パラメーター。  
  
   - パラメーターの型記述子。  
  
   - メソッドのメソッドのインスタンス。  
  
     詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
4. **ソリューション エクスプ ローラー**エンティティの場合に生成されたサービスのコード ファイルのショートカット メニューを開き、選択し、**コードの表示**します。  
  
    エンティティ サービス コード ファイルがコード エディターで開きます。 詳細については、エンティティ サービス コード ファイルは、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
5. レコードを削除する Deleter メソッドにコードを追加します。 次の例では、SQL Server の AdventureWorks サンプル データベースを使用して販売注文から品目を削除します。  
  
   > [!NOTE]  
   >  この例では、メソッドは、2 つの入力パラメーターを使用します。  
  
   > [!NOTE]  
   >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Updater メソッドの追加](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスの定義](../sharepoint/how-to-define-a-method-instance.md)  
  
  
