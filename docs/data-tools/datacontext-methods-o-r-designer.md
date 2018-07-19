---
title: DataContext メソッド (O/R デザイナー)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d8e3a39c79b5dee339c8835c78143277f3015f6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756130"
---
# <a name="datacontext-methods-or-designer"></a>DataContext メソッド (O/R デザイナー)

<xref:System.Data.Linq.DataContext> メソッド (のコンテキストで、 [LINQ to SQL ツール Visual Studio で](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) のメソッドは、<xref:System.Data.Linq.DataContext>データベースでストアド プロシージャおよび関数を実行するクラス。

<xref:System.Data.Linq.DataContext> クラスは、SQL Server データベースと、そのデータベースにマップされる [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラスの間のパイプ役として機能する [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスです。 <xref:System.Data.Linq.DataContext>クラスには、接続文字列の情報と、データベースに接続すると、データベース内のデータを操作するメソッドが含まれています。 既定で、<xref:System.Data.Linq.DataContext>クラスにはなど、呼び出すことのできるいくつかのメソッドが含まれています、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>を送信するメソッドからのデータを更新する[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]クラス、データベースにします。 作成することも追加<xref:System.Data.Linq.DataContext>ストアド プロシージャおよび関数にマップされるメソッド。 つまり、これらのカスタム メソッドを呼び出すストアド プロシージャまたは関数で実行、データベースを<xref:System.Data.Linq.DataContext>メソッドをマップします。 メソッドを追加して任意のクラスを拡張するのと同じように、<xref:System.Data.Linq.DataContext> クラスに新しいメソッドを追加できます。 ただし、に関するディスカッションで<xref:System.Data.Linq.DataContext>メソッドのコンテキストで、 **O/R デザイナー**は、<xref:System.Data.Linq.DataContext>ストアド プロシージャとは、説明されている関数にマップされるメソッド。

## <a name="methods-pane"></a>メソッド ペイン

<xref:System.Data.Linq.DataContext> ストアド プロシージャおよび関数にマップされるメソッドに表示される、**メソッド**のウィンドウ、 **O/R デザイナー**します。 **メソッド**ウィンドウは、ウィンドウの横に、**エンティティ**ウィンドウ (メインのデザイン画面)。 **メソッド**ウィンドウすべて一覧表示<xref:System.Data.Linq.DataContext>メソッドを使用して作成した、 **O/R デザイナー**します。 既定で、**メソッド**ペインは空ドラッグ ストアド プロシージャまたは関数から**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/r デザイナー。** を作成する<xref:System.Data.Linq.DataContext>メソッドを設定し、**メソッド**ウィンドウ。 詳細については、次を参照してください。[方法: ストアド プロシージャおよび関数 (O/r デザイナー) にマップされる DataContext の作成メソッド](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)します。

> [!NOTE]
> 右クリックし、メソッド ペインを開いたり閉じたり、 **O/R デザイナー**  をクリックし、**メソッド ペインの非表示に**または**メソッド ペインの表示**、キーボードショートカットを使用して、または**Ctrl キーを押し**+**1**します。

## <a name="two-types-of-datacontext-methods"></a>DataContext メソッドの 2 つの種類

DataContext メソッドは、データベース内のストアド プロシージャおよび関数にマップされるメソッドです。 作成してに DataContext メソッドを追加、**メソッド**のウィンドウ、 **O/R デザイナー**します。 2 種類の区別がある<xref:System.Data.Linq.DataContext>メソッドはそうでないものと 1 つまたは複数の結果セットを返すもの。

-   1 つ以上の結果セットを返す <xref:System.Data.Linq.DataContext> メソッド

     この種類の <xref:System.Data.Linq.DataContext> メソッドは、アプリケーションでデータベース内のストアド プロシージャおよび関数を実行し、結果を返すことだけが必要な場合に作成します。 詳細については、次を参照してください。[方法: ストアド プロシージャおよび関数 (O/r デザイナー) にマップされる DataContext の作成メソッド](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、System.Data.Linq.ISingleResult\<T >、および<xref:System.Data.Linq.IMultipleResults>します。

-   結果セットを返さない <xref:System.Data.Linq.DataContext> メソッド (特定のエンティティ クラスの挿入、更新、削除など)

     この種類の作成<xref:System.Data.Linq.DataContext>メソッド、アプリケーションがある既定値を使用する代わりにストアド プロシージャを実行する際に[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]保存の動作は、エンティティ クラスとデータベース間でデータを変更します。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。

## <a name="return-types-of-datacontext-methods"></a>DataContext メソッドの戻り値の型

ストアド プロシージャおよび関数からのドラッグと**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**、戻り値の型を生成された<xref:System.Data.Linq.DataContext>メソッドは、項目をドロップする場所によって異なります。 作成、既存のエンティティ クラスに直接の項目をドロップする、<xref:System.Data.Linq.DataContext>エンティティ クラスの戻り値の型を持つメソッドは項目をドロップの空の領域、 **O/R デザイナー** (いずれかのウィンドウ) では、作成、<xref:System.Data.Linq.DataContext>メソッド返す、自動的に生成された型です。 自動生成された型は、ストアド プロシージャまたは関数名とプロパティは、ストアド プロシージャまたは関数によって返されるフィールドのマッピングと一致する名前を持ちます。

> [!NOTE]
> <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、検査、**戻り値の型**プロパティ、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[方法: DataContext メソッド (O/r デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)します。

O/R デザイナー画面上にデータベースからドラッグしたオブジェクトは、データベース内のオブジェクトの名前に基づいて、自動的に命名されます。 同じオブジェクトを複数回ドラッグすると、数値は、名前を識別する新しい名前の末尾に追加されます。 データベース オブジェクト名にスペースや Visual Basic または C# でサポートされない文字が含まれている場合、そのスペースまたは無効な文字はアンダースコアに置き換えられます。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [ストアド プロシージャ](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [チュートリアル : エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)