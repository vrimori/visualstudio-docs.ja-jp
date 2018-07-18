---
title: TableAdapter を使用してデータを更新します。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fba0258839af6675f07c0962ee4281516dce3295
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921577"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter を使用してデータを更新します。

データセット内のデータを変更して検証後に送信できます、更新されたデータをデータベースに戻すを呼び出して、`Update`のメソッド、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)です。 `Update`メソッドを 1 つのデータ テーブルを更新して、に基づいて正しいコマンド (INSERT、UPDATE、または DELETE) を実行、<xref:System.Data.DataRow.RowState%2A>テーブル内の各データ行のです。 データセット関連テーブルがあるときに、Visual Studio は、更新プログラムを実行するために使用 TableAdapterManager クラスを生成します。 TableAdapterManager クラスにより、更新プログラムがデータベースで定義されている外部キー制約に基づく正しい順序で行われること。 データ バインド コントロールを使用する場合、データ バインディング アーキテクチャは、tableAdapterManager と呼ばれる TableAdapterManager クラスのメンバー変数を作成します。

> [!NOTE]
> データセットの内容でデータ ソースを更新しようとすると、エラーが発生することができます。エラーを回避することをお勧め、アダプターを呼び出すコードを配置すること`Update`メソッドの中、 `try` / `catch`ブロックします。

 データ ソースを更新する詳細な手順は、ビジネス ニーズによって異なることができますが、次の手順が含まれています。

1.  呼び出し、アダプターの`Update`メソッドで、 `try` / `catch`ブロックします。

2.  例外が検出された場合は、エラーを引き起こしたデータ行を探します。

3.  データの問題を調整 (プログラムですることはできますかに無効な行を変更するためのユーザーに提示することにより) を行し、更新プログラムをもう一度やり直して (<xref:System.Data.DataRow.HasErrors%2A>、 <xref:System.Data.DataTable.GetErrors%2A>)。

## <a name="save-data-to-a-database"></a>データをデータベースに保存します。

呼び出す、 `Update` TableAdapter のメソッドです。 データベースに書き込まれる値を含むデータ テーブルの名前を渡します。

### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter を使用してデータベースを更新するには

-   TableAdapter を囲む`Update`メソッドで、 `try` / `catch`ブロックします。 次の例の内容を更新する方法を示しています、`Customers`テーブルに`NorthwindDataSet`内から、 `try` / `catch`ブロックします。

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)