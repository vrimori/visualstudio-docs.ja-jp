---
title: '方法: テーブルとビューにマップされた LINQ to SQL クラスを作成する (O-R デザイナー)'
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
ms.openlocfilehash: b66559061f0d66699a7505c71541b237814812c4
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305599"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>方法: テーブルとビューにマップされた LINQ to SQL クラスを作成する (O/R デザイナー)

データベース テーブルおよびビューにマップされた [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスは、*エンティティ クラス*と呼ばれます。 エンティティ クラスはレコードにマップされますが、エンティティ クラスの個々のプロパティはレコードを構成する個々の列にマップされます。 テーブルまたはビューをドラッグしてデータベース テーブルまたはビューに基づくエンティティ クラスを作成**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 [のVisualStudioでのLINQtoSQLツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **O/R デザイナー**クラスを生成し、特定の適用[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]属性を有効にする[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]機能 (データ通信編集および編集の機能、 <xref:System.Data.Linq.DataContext>)。 詳細については[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]クラスを参照してください[LINQ to SQL オブジェクト モデル](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)します。

> [!NOTE]
> **O/R デザイナー**簡単なオブジェクト リレーショナル マッパーは、1 対 1 のマッピング関係のみをサポートしているためです。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 1 つのエンティティ クラスを複数のテーブルにマップするなど、複雑なマッピングはサポートされていません。 ただし、複数の関連テーブルを結合するビューにエンティティ クラスをマップすることはできます。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスの作成

テーブルまたはビューからドラッグ**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**に加え、エンティティ クラスを作成し、<xref:System.Data.Linq.DataContext>メソッドを更新プログラムを実行するために使用されます。

既定では、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムによって、更新可能なエンティティ クラスの変更をデータベースに保存するロジックが作成されます。 このロジックは、テーブルのスキーマ (列定義と主キー情報) に基づいています。 この動作が不要な場合は、既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作の代わりに、ストアド プロシージャを使用して挿入、更新、削除を実行するようにエンティティ クラスを構成できます。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスを作成するには

1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、**[テーブル]** または **[ビュー]** を展開し、アプリケーションで使用するデータベース テーブルまたはビューを探します。

2.  テーブルをドラッグするか、上に表示、 **O/R デザイナー**します。

     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。 このエンティティ クラスには、選択されたテーブルまたはビューの列にマップされるプロパティが含まれています。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>オブジェクト データ ソースの作成とフォームへのデータの表示

使用してエンティティ クラスを作成した後、 **O/R デザイナー**、オブジェクト データ ソースを作成して設定できる、[データ ソース ウィンドウ](add-new-data-sources.md#data-sources-window)エンティティ クラスを使用します。

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL エンティティ クラスに基づいてオブジェクト データ ソースを作成するには

1.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックしてプロジェクトをビルドします。

2.  開くには、**データ ソース**ウィンドウで、**データ**] メニューのをクリックして **[データ ソースの**します。

3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

4.  **[データソースの種類を選択]** ページで、**[オブジェクト]** をクリックし、**[次へ]** をクリックします。

5.  ノードを展開し、クラスを探して選択します。

    > [!NOTE]
    > **Customer** クラスが使用可能でない場合は、ウィザードをキャンセルし、プロジェクトをビルドしてからウィザードを再実行します。

6.  **[完了]** をクリックしてデータ ソースを作成し、**Customer** エンティティ クラスを **[データ ソース]** ウィンドウに追加します。

7.  **[データ ソース]** ウィンドウからフォームに項目をドラッグします。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラスの作成 (O-R デザイナー)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: ストアド プロシージャや関数にマップされる DataContext メソッドを作成する (O/R デザイナー)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL オブジェクト モデル](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [チュートリアル : エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [方法: LINQ to SQL クラス間の関連付け (リレーションシップ) を作成する (O/R デザイナー)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)