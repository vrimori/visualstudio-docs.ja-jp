---
title: '方法: Finder メソッドの追加 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ae5b1dfca8a083f12aa05d96378c3df348766a0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872886"
---
# <a name="how-to-add-a-finder-method"></a>方法: Finder メソッドを追加します。
  Web パーツまたは一覧内のエンティティの一覧を表示するビジネス データ接続 (BDC) サービスを有効にすることを作成する必要があります、 *Finder*メソッド。 Finder メソッドは、エンティティ インスタンスのコレクションを返す特殊なメソッドです。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
### <a name="to-create-a-finder-method"></a>Finder メソッドを作成するには  
  
1. **BDC デザイナー**エンティティを選択します。  
  
    詳細については、「[方法 :エンティティ モデルを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)します。  
  
2. メニュー バーで、**ビュー** > **その他の Windows** > **BDC メソッドの詳細**します。  
  
    **BDC メソッドの詳細**ウィンドウが開きます。 詳細については、 **BDC メソッドの詳細**ウィンドウを参照してください[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)します。  
  
3. **メソッドを追加する**一覧で、選択**Finder メソッドの作成**です。  
  
    Visual Studio では、メソッド、戻りパラメーター、および型記述子を追加します。  
  
4. エンティティ コレクション型記述子としては、型記述子を構成します。 エンティティ コレクション型記述子を作成する方法の詳細については、次を参照してください。[方法。パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)します。  
  
   > [!NOTE]  
   >  エンティティの Specificfinder メソッドを追加した場合、この手順を実行する必要はありません。 Visual Studio では、Specificfinder メソッドで定義した型記述子を使用します。  
  
5. **ソリューション エクスプ ローラー**エンティティの場合に生成されたサービスのコード ファイルのショートカット メニューを開き、選択し、**コードの表示**します。 サービス コード ファイルの詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
6. Finder メソッドにコードを追加します。 このコードは次のタスクを実行します。  
  
   - データ ソースからデータを取得します。  
  
   - BDC サービスにエンティティの一覧を返します。  
  
     次の例のコレクションを返します`Contact`SQL Server の AdventureWorks サンプル データベースからデータを使用してエンティティ。  
  
   > [!NOTE]  
   >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>関連項目
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [方法: 特定の Finder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加します。](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加します。](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加します。](../sharepoint/how-to-add-an-updater-method.md)   
 [方法: メソッドにパラメーターを追加します。](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: メソッド インスタンスを定義します。](../sharepoint/how-to-define-a-method-instance.md)  
