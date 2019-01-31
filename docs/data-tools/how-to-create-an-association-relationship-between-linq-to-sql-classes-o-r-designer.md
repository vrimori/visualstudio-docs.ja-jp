---
title: LINQ to SQL クラスを O/R デザイナーを使用して間リレーションシップを作成する方法
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ab66f41a6510eb8cf2376cb7bb4d6fa21e7b1159
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001331"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>方法: LINQ to SQL クラス (O/R デザイナー) 間のアソシエーションを作成します。
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] のエンティティ クラス間の関連付けは、データベース内のテーブル間の関連付けに似ています。 **[関連付けエディター]** ダイアログ ボックスを使用することで、エンティティ クラス間の関連付けを作成できます。

**[関連付けエディター]** ダイアログ ボックスを使用して関連付けを作成するときは、親クラスと子クラスを選択する必要があります。 親クラスは、主キーを含むエンティティ クラスであり、子クラスは、外部キーを含むエンティティ クラスです。 たとえば、エンティティ クラスには、そのマップが作成された場合、`Northwind Customers`と`Orders`テーブル、`Customer`クラスは、親クラスになります、`Order`クラスは、子クラスになります。

> [!NOTE]
>  テーブルをドラッグすると**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、**オブジェクト リレーショナル デザイナー** (**O/R デザイナー**)、アソシエーションは、データベース内の既存の外部キー リレーションシップに基づいて自動的に作成されます。

## <a name="association-properties"></a>関連付けのプロパティ
関連付けの作成後、**O/R デザイナー**で関連付けを選択すると、**[プロパティ]** ウィンドウにいくつかの構成可能なプロパティが表示されます。 関連付けは、関連クラス間の線で表されます。次の表は、関連付けのプロパティの説明を示しています。

|プロパティ|説明|
|--------------|-----------------|
|**カーディナリティ**|関連付けが 1 対多と 1 対 1 のどちらであるかを制御します。|
|**子プロパティ**|コレクションのプロパティを親に作成するか、子レコードへの参照を関連付けの外部キー側に作成するかを指定します。 間の関連付けなどで`Customer`と`Order`場合、**子プロパティ**に設定されている**True**、という名前のプロパティ`Orders`親クラスに作成されます。|
|**親プロパティ**|関連付けられている親クラスを参照する子クラスのプロパティです。 間の関連付けなどで`Customer`と`Order`、という名前のプロパティ`Customer`で注文が作成されたに関連付けられている顧客を参照する、`Order`クラス。|
|**関与のプロパティ**|関連付けのプロパティを表示し、**[関連付けエディター]** ダイアログ ボックスを再び開く**省略記号**ボタン (...) が用意されています。|
|**一意**|外部ターゲット列に一意性の制約があるかどうかを示します。|

## <a name="to-create-an-association-between-entity-classes"></a>エンティティ クラス間に関連付けを作成するには

1.  関連付けの親クラスを表すエンティティ クラスを右クリックし、**[追加]** をポイントして、**[関連付け]** をクリックします。

2.  **[関連付けエディター]** ダイアログ ボックスで、正しい**親クラス**が選択されていることを確認します。

3.  コンボ ボックスで**子クラス**を選択します。

4.  クラスに関連する **[関連付けのプロパティ]** を選択します。 通常、これはデータベースで定義されている外部キー リレーションシップにマップされます。 など、`Customers`と`Orders`アソシエーション、**関連付けのプロパティ**は、`CustomerID`クラスごとにします。

5.  **[OK]** をクリックして、関連付けを作成します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラスを作成](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: 主キーを表す](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)