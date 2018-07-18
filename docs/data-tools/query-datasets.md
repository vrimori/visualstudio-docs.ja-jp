---
title: クエリのデータセット
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0fb1310649a1aeba7fd46acf9277ef7ea5825472
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926701"
---
# <a name="query-datasets"></a>クエリのデータセット
データセット内の特定のレコードを検索する DataTable で FindBy メソッドを使用して、独自 foreach ステートメントを使用したり、テーブルの行のコレクションをループを記述[LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)です。

## <a name="dataset-case-sensitivity"></a>データセットの大文字と小文字の区別
テーブルおよび列名が既定では大文字と小文字は、データセット内で、つまり、「顧客」をという名前のデータセット内のテーブルも呼ばれますに"customers"として これには、SQL Server を含む、多くのデータベースでの名前付け規則と一致します。 SQL Server の既定の動作は、データ要素の名前を大文字小文字によってのみ区別されないことです。

> [!NOTE]
>  データセットとは異なりスキーマで定義されたデータ要素の名前は大文字小文字を区別するための XML ドキュメントが、大文字小文字を区別します。 たとえば、スキーマのプロトコルは「顧客」、"customers"と呼ばれる別のテーブルと呼ばれるテーブルを定義するスキーマを使用できます。 大文字と小文字が異なるだけの要素を含むスキーマを使用して dataset クラスを生成すると、名前の競合、これがあります。

ただし、大文字小文字の区別は、データセット内のデータを解釈する方法の係数を指定できます。 たとえば、データセット テーブル内のデータをフィルター処理する検索条件は、比較では大文字小文字を区別するかどうかに応じて異なる結果を返す可能性があります。 フィルター処理、検索、およびデータセットの並べ替えの大文字小文字の区別を制御する<xref:System.Data.DataSet.CaseSensitive%2A>プロパティです。 データセット内のすべてのテーブルは、既定では、このプロパティの値を継承します。 (個別のテーブルに対してこのプロパティをオーバーライドするには、テーブルを設定して<xref:System.Data.DataTable.CaseSensitive%2A>プロパティです)。

## <a name="locate-a-specific-row-in-a-data-table"></a>データ テーブル内で特定の行を検索します。

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>主キーの値と型指定されたデータセットの行を検索するには

-   行を見つけるには、厳密に型指定呼び出す`FindBy`テーブルの主キーを使用するメソッド。

     次の例で、`CustomerID`列の主キーである、`Customers`テーブル。 つまり、生成された`FindBy`メソッドは`FindByCustomerID`します。 例を固有の仕様を割り当てる方法を示します<xref:System.Data.DataRow>、生成されたを使用して変数に`FindBy`メソッドです。

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>主キー値を持つデータセットの行を検索するには

-   呼び出す、<xref:System.Data.DataRowCollection.Find%2A>のメソッド、<xref:System.Data.DataRowCollection>コレクション、パラメーターとして、主キーを渡します。

     次の例と呼ばれる新しい行を宣言する方法を示しています。`foundRow`の戻り値を割り当てると、<xref:System.Data.DataRowCollection.Find%2A>メソッドです。 主キーが見つかった場合、列インデックス 1 の内容は、メッセージ ボックスに表示されます。

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>列の値で行を検索します。

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>任意の列の値に基づいて行を検索するには

-   データ テーブルが作成された、<xref:System.Data.DataTable.Select%2A>の配列を返すメソッド<xref:System.Data.DataRow>に渡される式に基づく s、<xref:System.Data.DataTable.Select%2A>メソッドです。 有効な式の作成の詳細については、ページの「式の構文」セクションを参照して、<xref:System.Data.DataColumn.Expression%2A>プロパティです。

     次の例を使用する方法を示しています、<xref:System.Data.DataTable.Select%2A>のメソッド、<xref:System.Data.DataTable>を特定の行を検索します。

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>関連するレコードのアクセス
データセット内のテーブルを関連すると、ときに、<xref:System.Data.DataRelation>オブジェクト、関連するレコード使用できるように、別のテーブルです。 たとえば、データセットを含む、`Customers`と`Orders`テーブルを使用できます。

使用することができます、<xref:System.Data.DataRelation>を呼び出して、関連するレコードを検索するオブジェクト、<xref:System.Data.DataRow.GetChildRows%2A>のメソッド、<xref:System.Data.DataRow>親テーブルにします。 このメソッドは、関連する子レコードの配列を返します。 呼び出すか、または、<xref:System.Data.DataRow.GetParentRow%2A>のメソッド、<xref:System.Data.DataRow>子テーブルにします。 このメソッドは、1 つを返します<xref:System.Data.DataRow>親テーブルからです。

このページは、型指定されたデータセットを使用する例を示します。 型指定されていないデータセットのリレーションシップを移動する方法については、次を参照してください。 [Datarelation の移動](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)です。

> [!NOTE]
>  Windows フォーム アプリケーションで作業するいるし、データ バインディング機能を使用して、データを表示する、デザイナーで生成されるフォームは、アプリケーションのための十分な機能を提供可能性があります。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)です。 具体的を参照してください[データセットのリレーションシップ](relationships-in-datasets.md)です。

次のコード例では、型指定されたデータセットのリレーションシップを上下に移動する方法を示します。 型指定されたコードの例として使用<xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) し、生成された FindBy*PrimaryKey* (`FindByCustomerID`) を目的の行を見つけて、関連するレコードを返すメソッド。 例をコンパイルしている場合にのみ正しく実行します。

-   という名前のデータセットのインスタンス`NorthwindDataSet`で、`Customers`テーブル。

-   `Orders`テーブル。

-   という名前のリレーションシップ`FK_Orders_Customers`2 つのテーブルに関連します。

さらに、両方のテーブルは、返されるレコードにデータを格納する必要があります。

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>選択された親レコードのレコードの子を取得するには

-   呼び出す、<xref:System.Data.DataRow.GetChildRows%2A>特定のメソッド`Customers`データ行をしてからの行の配列を返す、`Orders`テーブル。

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>選択されている子レコードの親レコードを取得するには

-   呼び出す、<xref:System.Data.DataRow.GetParentRow%2A>特定のメソッド`Orders`データ行、および戻り値の 1 つの行、`Customers`テーブル。

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>関連項目

- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)