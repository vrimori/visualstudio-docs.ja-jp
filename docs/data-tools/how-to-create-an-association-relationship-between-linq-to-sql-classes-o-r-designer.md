---
title: LINQ to SQL クラスを O/R デザイナーを使用して、リレーションシップを作成する方法 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: caf084ea7c3d4fdf9d793d279669c4114bfd81d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>方法: LINQ to SQL クラス (O/R デザイナー) 間の関連付けを作成します。
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] のエンティティ クラス間の関連付けは、データベース内のテーブル間の関連付けに似ています。 使用してエンティティ クラス間の関連付けを作成することができます、 **[関連付けエディター** ] ダイアログ ボックス。  
  
使用すると、親クラスと子クラスを選択する必要があります、 **[関連付けエディター**関連付けを作成する] ダイアログ ボックス。 親クラスは、主キーを含むエンティティ クラスであり、子クラスは、外部キーを含むエンティティ クラスです。 たとえば、Northwind の Customers テーブルと Orders テーブルにマップされるエンティティ クラスが作成された場合は、Customer クラスが親クラスであり、Order クラスが子クラスです。  
  
> [!NOTE]
>  テーブルをドラッグすると**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)])、アソシエーションが既存のに基づいて自動的に作成データベース内の外部キー リレーションシップです。  

## <a name="association-properties"></a>関連付けのプロパティ
いくつかの構成可能なプロパティがある、O/R デザイナーで関連付けを選択すると、関連付けを作成した後、**プロパティ**ウィンドウです。 関連付けは、関連クラス間の線で表されます。次の表は、関連付けのプロパティの説明を示しています。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**基数**|関連付けが 1 対多と 1 対 1 のどちらであるかを制御します。|  
|**子プロパティ**|コレクションのプロパティを親に作成するか、子レコードへの参照を関連付けの外部キー側に作成するかを指定します。 たとえば、Customer と Order 間の関連付けの場合、**子プロパティ**に設定されている**True**、Orders という名前のプロパティが親クラスを作成します。|  
|**親プロパティ**|関連付けられている親クラスを参照する子クラスのプロパティです。 たとえば、Customer と Order の間の関連付けでは、注文に関連付けられている顧客を参照する Customer という名前のプロパティが Order クラスに作成されます。|  
|**関与のプロパティ**|関連付けのプロパティが表示され、**省略記号**を再び開くボタン (...)、 **関連付けエディター**  ダイアログ ボックス。|  
|**一意**|外部ターゲット列に一意性の制約があるかどうかを示します。|  
  
## <a name="to-create-an-association-between-entity-classes"></a>エンティティ クラス間に関連付けを作成するには
  
1.  関連付けの親クラスを表すエンティティ クラスを右クリックし、順にポイント**追加**、クリックして**アソシエーション**です。  
  
2.  いることを確認、正しい**親クラス**でが選択されている、 **[関連付けエディター** ] ダイアログ ボックス。  
  
3.  選択、**子クラス**コンボ ボックスにします。  
  
4.  選択、**関連付けのプロパティ**クラスに関連します。 通常、これはデータベースで定義されている外部キー リレーションシップにマップされます。 たとえば、Customers と Orders の関連付けで、**関連付けのプロパティ**は各クラスの CustomerID にします。  
  
5.  をクリックして**OK**関連付けを作成します。  
  
## <a name="see-also"></a>関連項目
[LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[チュートリアル: LINQ to SQL クラスを作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
[方法 : 主キーを表す](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)