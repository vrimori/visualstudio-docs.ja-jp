---
title: "方法: Finder メソッドにフィルター記述子を追加 |Microsoft ドキュメント"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37aff0510af501b75aafe190fc412a0d4b9fd625
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>方法: Finder メソッドにフィルター記述子を追加する
  フィルター記述子には、値を渡すメソッドを実行する前に、モデルのコンシューマーが有効にします。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
 1 つの一般的なシナリオは、SharePoint 内のユーザーがいくつかの条件に一致する外部コンテンツ タイプのインスタンスを取得することです。 Finder メソッドにフィルター記述子を追加することで、このシナリオをサポートできます。  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Finder メソッドにフィルター記述子を追加するには  
  
1.  **BDC メソッドの詳細**ウィンドウ、Finder メソッドのノードを展開し、**パラメーター**ノード、し、入力パラメーターを追加します。 詳細については、次を参照してください。[する方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)です。  
  
2.  **メソッドの詳細**ウィンドウで、パラメーターの型記述子を選択します。  
  
3.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。  
  
4.  **プロパティ**ウィンドウで、設定、**型名**プロパティをフィルターを適切なデータ型。  
  
     たとえば、フィルターで注文日を使用して、メソッドによって返される販売注文数を制限する可能性があります。 そのフィルターをサポートするために、**型名**に、型記述子のプロパティを設定する必要があります**System.DateTime**です。  
  
5.  **メソッドの詳細**ウィンドウで、展開、**フィルター記述子**ノード。  
  
6.  **フィルター記述子を追加**一覧で、選択**フィルター記述子の作成**です。  
  
     新しいフィルター記述子が下に表示されます、**フィルター記述子**ノード。  
  
7.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。  
  
8.  **プロパティ**ウィンドウで、選択、**型**プロパティです。  
  
9. に対して表示される一覧で、**型**プロパティかフィルター パターンを選択します。  
  
     たとえば、注文日を使用して Finder メソッドで返される販売注文の数を制限するフィルターを作成する次のように選択します。**比較**です。 比較フィルターでは、finder メソッドを特定の条件を満たすインスタンスのみを返すことを保証します。 各フィルター パターンの詳細については、次を参照してください。[型のフィルターでサポート、BDC](http://go.microsoft.com/fwlink/?LinkId=169287)です。  
  
10. **プロパティ**ウィンドウで、選択、**関連付けられた型記述子**プロパティです。  
  
11. 表示される一覧で、**型記述子の関連付けられている**プロパティでは、この手順の前半で作成した型記述子を選択します。 これにより、フィルターが Finder メソッドの入力パラメーターに関連しています。  
  
12. データを返す Finder メソッドにコードを追加します。 Select クエリの条件として入力パラメーターを使用することができます。  
  
     次の例では、指定した注文日の販売注文を返します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: Specificfinder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: パラメーターの型記述子を定義します。](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [ビジネス データ接続モデルの設計](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  