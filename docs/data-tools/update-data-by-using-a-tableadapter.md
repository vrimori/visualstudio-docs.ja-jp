---
title: TableAdapter を使用してデータを更新する
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
ms.workload:
- data-storage
ms.openlocfilehash: fda8f23cdaff6fc98e0a0bb982d5c4c17265ecf0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843282"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter を使用してデータを更新する

データセット内のデータを変更して検証した後のデータベースの更新されたデータを送信呼び出すことによって、`Update`のメソッド、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)します。 `Update`メソッドを 1 つのデータ テーブルを更新してに基づいて適切なコマンド (INSERT、UPDATE、または DELETE) の実行、<xref:System.Data.DataRow.RowState%2A>表内の各データ行のできます。 データセットの関連するテーブルが、Visual Studio は、更新プログラムを実行するために使用 TableAdapterManager クラスを生成します。 TableAdapterManager クラスにより、データベースで定義されている外部キー制約に基づく正しい順序で更新が行われるようになります。 データ バインド コントロールを使用すると、データ バインディング アーキテクチャには、tableAdapterManager と呼ばれる TableAdapterManager クラスのメンバー変数が作成されます。

> [!NOTE]
> データセットの内容でデータ ソースを更新しようとするときにエラーが発生することができます。 エラーを回避するをお勧め、アダプターを呼び出すコードを配置する`Update`メソッド内で、 `try` / `catch`ブロックします。

 データ ソースを更新するための実際の手順は、ビジネス ニーズによって異なることができますが、次の手順が含まれています。

1.  アダプターの呼び出す`Update`メソッドで、 `try` / `catch`ブロック。

2.  例外が検出された場合は、エラーを引き起こしたデータ行を探します。

3.  データの問題を調整 (プログラムを使用できる場合、または無効な行を変更するためのユーザーに提示することで) 行、および更新プログラムをもう一度やり直して (<xref:System.Data.DataRow.HasErrors%2A>、 <xref:System.Data.DataTable.GetErrors%2A>)。

## <a name="save-data-to-a-database"></a>データをデータベースに保存します。

呼び出す、 `Update` TableAdapter のメソッド。 データベースに書き込まれる値を含むデータ テーブルの名前を渡します。

### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter を使用してデータベースを更新するには

-   TableAdapter を囲む`Update`メソッドで、 `try` / `catch`ブロックします。 次の例の内容を更新する方法を示しています、`Customers`テーブルに`NorthwindDataSet`内から、 `try` / `catch`ブロックします。

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)