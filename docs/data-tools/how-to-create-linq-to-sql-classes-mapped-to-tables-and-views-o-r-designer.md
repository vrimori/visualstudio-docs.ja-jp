---
title: '方法: LINQ to SQL クラスのテーブルとビュー (O/R デザイナー) にマップを作成'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089326"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>方法: LINQ to SQL クラスのテーブルとビュー (O/R デザイナー) にマップを作成
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] データベース テーブルおよびビューにマップされているクラスと呼ばれます*エンティティ クラス*します。 エンティティ クラスはレコードにマップされますが、エンティティ クラスの個々のプロパティはレコードを構成する個々の列にマップされます。 テーブルまたはビューをドラッグしてデータベース テーブルまたはビューに基づくエンティティ クラスを作成**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 [のVisualStudioでのLINQtoSQLツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **O/R デザイナー**クラスを生成し、特定の適用[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]属性を有効にする[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]機能 (データ通信編集および編集の機能、 <xref:System.Data.Linq.DataContext>)。 詳細については[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]クラスを参照してください[LINQ to SQL オブジェクト モデル](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)します。

> [!NOTE]
>  **O/R デザイナー**簡単なオブジェクト リレーショナル マッパーは、1 対 1 のマッピング関係のみをサポートしているためです。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 1 つのエンティティ クラスを複数のテーブルにマップするなど、複雑なマッピングはサポートされていません。 ただし、複数の関連テーブルを結合するビューにエンティティ クラスをマップすることはできます。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>LINQ to SQL クラスのデータベース テーブルまたはビューにマップされている作成します。
 テーブルまたはビューからドラッグ**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**に加え、エンティティ クラスを作成し、<xref:System.Data.Linq.DataContext>メソッドを更新プログラムを実行するために使用されます。

 既定では、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムによって、更新可能なエンティティ クラスの変更をデータベースに保存するロジックが作成されます。 このロジックは、テーブルのスキーマ (列定義と主キー情報) に基づいています。 この動作をしない場合は、ストアド プロシージャを使用して、挿入、更新、および既定値を使用する代わりに、削除を実行するエンティティ クラスを構成できます[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]実行時の動作。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスを作成するには

1.  **Server**または**データベース エクスプ ローラー**、展開**テーブル**または**ビュー**とデータベースのテーブルを検索または表示で使用する、アプリケーション。

2.  テーブルをドラッグするか、上に表示、 **O/R デザイナー**します。

     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。 このエンティティ クラスには、選択されたテーブルまたはビューの列にマップされるプロパティが含まれています。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>オブジェクト データ ソースを作成し、フォームにデータを表示
 使用してエンティティ クラスを作成した後、 **O/R デザイナー**、オブジェクト データ ソースを作成して設定できる、[データ ソース ウィンドウ](add-new-data-sources.md)エンティティ クラスを使用します。

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL エンティティ クラスに基づいてオブジェクト データ ソースを作成するには

1.  **ビルド** メニューのをクリックして**ソリューションのビルド**プロジェクトをビルドします。

2.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

4.  をクリックして**オブジェクト**で、**データ ソースの種類を選択**ページをクリックして**次**。

5.  ノードを展開し、クラスを探して選択します。

    > [!NOTE]
    >  場合、**顧客**クラスは使用できません、ウィザードをキャンセル、プロジェクトをビルド、およびウィザードを再度実行します。

6.  をクリックして**完了**、データ ソースを作成し、追加、**顧客**エンティティ クラスを**データ ソース**ウィンドウ。

7.  項目をドラッグ、**データソース**ウィンドウからフォームにします。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL オブジェクト モデル](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [チュートリアル : エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [方法: LINQ to SQL クラス (O/R デザイナー) の間の関連付け (リレーションシップ) の作成](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)