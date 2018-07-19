---
title: '方法: Finder メソッドにフィルター記述子の追加 |Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63374f4d96c86ea3eafbd4c6fa3fbe3d1f5a5899
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755600"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>方法: Finder メソッドにフィルター記述子の追加
  フィルター記述子には、実行する前に、メソッドに値を渡すためのモデルのコンシューマーが有効にします。 詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
 1 つの一般的なシナリオは、SharePoint 内のユーザーがいくつかの条件に一致する外部コンテンツ タイプのインスタンスを取得することです。 Finder メソッドにフィルター記述子を追加することで、このシナリオをサポートできます。  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Finder メソッドにフィルター記述子を追加するには  
  
1.  **BDC メソッドの詳細**ウィンドウで、Finder メソッドのノードを展開、展開、**パラメーター**ノード、し、入力パラメーターを追加します。 詳細については、次を参照してください。[方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)します。  
  
2.  **メソッドの詳細**ウィンドウで、パラメーターの型記述子を選択します。  
  
3.  メニュー バーで、**ビュー** > **プロパティ ウィンドウ**します。  
  
4.  **プロパティ**ウィンドウで、設定、**型名**プロパティをフィルターの適切なデータ型。  
  
     たとえば、フィルターで注文日を使用して、メソッドによって返される販売注文の数を制限する可能性があります。 そのフィルターをサポートするために、**型名**に、型記述子のプロパティを設定する必要があります**System.DateTime**します。  
  
5.  **メソッドの詳細**ウィンドウで、展開、**フィルター記述子**ノード。  
  
6.  **フィルター記述子を追加**一覧で、選択**フィルター記述子の作成**です。  
  
     新しいフィルター記述子が下に表示されます、**フィルター記述子**ノード。  
  
7.  メニュー バーで、**ビュー** > **プロパティ ウィンドウ**します。  
  
8.  **プロパティ**ウィンドウで、選択、**型**プロパティ。  
  
9. 表示される一覧で、**型**プロパティ、フィルターのパターンを選択します。  
  
     たとえば、注文日を使用して、Finder メソッドで返される販売注文の数を制限するフィルターを作成するには、次のように選択します。**比較**します。 比較フィルターにより、finder メソッドが特定の条件を満たすインスタンスのみを返します。 各フィルター パターンの詳細については、次を参照してください。[のフィルターでサポートされる型、BDC](http://go.microsoft.com/fwlink/?LinkId=169287)します。  
  
10. **プロパティ**ウィンドウで、選択、**関連付けられた型記述子**プロパティ。  
  
11. 表示される一覧で、**関連付けられた型記述子**プロパティでは、この手順の前半で作成した型記述子を選択します。 これには、Finder メソッドの入力パラメーターに、フィルターが関連しています。  
  
12. データを返す Finder メソッドにコードを追加します。 Select クエリの条件として入力パラメーターを使用することができます。  
  
     次の例では、指定した注文日の販売注文を返します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>関連項目
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: メソッドにパラメーターを追加](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [方法: パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [SharePoint にビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
