---
title: DataContext メソッド (O R デザイナー)
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
ms.openlocfilehash: 4f3cd7db587c940b4d310f6354f83983aae659fb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="datacontext-methods-or-designer"></a>DataContext メソッド (O/R デザイナー)

<xref:System.Data.Linq.DataContext> メソッド (のコンテキストで、 [LINQ to SQL ツール Visual Studio で](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) のメソッドは、<xref:System.Data.Linq.DataContext>データベースでストアド プロシージャと関数を実行するクラス。

<xref:System.Data.Linq.DataContext> クラスは、SQL Server データベースと、そのデータベースにマップされる [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラスの間のパイプ役として機能する [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスです。 <xref:System.Data.Linq.DataContext>クラスには、接続文字列の情報と、データベースに接続して、データベース内のデータを操作するためのメソッドが含まれています。 既定では、<xref:System.Data.Linq.DataContext>クラスには、いくつかのメソッド呼び出すことができるなどにはが含まれています、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>を送信するメソッドから更新されたデータ[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]データベースへのクラスです。 作成することも追加<xref:System.Data.Linq.DataContext>ストアド プロシージャおよび関数にマップされるメソッド。 つまり、これらのカスタム メソッドを呼び出すと、<xref:System.Data.Linq.DataContext> メソッドのマップ先となっているデータベース内のストアド プロシージャまたは関数が実行されます。 メソッドを追加して任意のクラスを拡張するのと同じように、<xref:System.Data.Linq.DataContext> クラスに新しいメソッドを追加できます。 ただし、に関するディスカッションに<xref:System.Data.Linq.DataContext>メソッドのコンテキストで、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]は、<xref:System.Data.Linq.DataContext>ストアド プロシージャおよびについては説明されている関数にマップされるメソッド。

## <a name="methods-pane"></a>メソッド ペイン

ストアド プロシージャおよび関数にマップされる <xref:System.Data.Linq.DataContext> メソッドは、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のメソッド ペインに表示されます。 メソッド ペインは、ウィンドウの横に、**エンティティ**ウィンドウ (メインのデザイン サーフェイス)。 メソッド ペインには、すべて一覧表示<xref:System.Data.Linq.DataContext>メソッドを使用して作成した、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 既定では、メソッド ペインは空です。ストアド プロシージャまたは関数をドラッグして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を作成する<xref:System.Data.Linq.DataContext>メソッドと、メソッド ペインが設定します。 詳細については、次を参照してください。[する方法: ストアド プロシージャおよび関数 (O/r デザイナー) にマップされる DataContext の作成メソッド](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)です。

> [!NOTE]
> 右クリックして、メソッド ペインを開いたり閉じたり、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]クリックし、**メソッド ペインの非表示に**または**メソッド ペイン**、またはキーボード ショートカット CTRL + 1 を使用します。

## <a name="two-types-of-datacontext-methods"></a>2 種類の DataContext メソッド

DataContext メソッドは、データベース内のストアド プロシージャおよび関数にマップされるメソッドです。 DataContext メソッドは、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のメソッド ペインで作成および追加できます。 2 種類の区別がある<xref:System.Data.Linq.DataContext>メソッド以外の場合は、1 つまたは複数の結果セットを返すと、そうでないです。

-   1 つ以上の結果セットを返す <xref:System.Data.Linq.DataContext> メソッド

     この種類の <xref:System.Data.Linq.DataContext> メソッドは、アプリケーションでデータベース内のストアド プロシージャおよび関数を実行し、結果を返すことだけが必要な場合に作成します。 詳細については、次を参照してください。[する方法: ストアド プロシージャおよび関数 (O/r デザイナー) にマップされる DataContext の作成メソッド](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、System.Data.Linq.ISingleResult\<T >、および<xref:System.Data.Linq.IMultipleResults>です。

-   結果セットを返さない <xref:System.Data.Linq.DataContext> メソッド (特定のエンティティ クラスの挿入、更新、削除など)

     この種類の作成<xref:System.Data.Linq.DataContext>メソッドは、アプリケーションには、既定値を使用する代わりにストアド プロシージャを実行すると[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]保存の動作は、エンティティ クラスとデータベース間でデータを変更します。 詳細については、次を参照してください。[する方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)です。

## <a name="return-types-of-datacontext-methods"></a>DataContext メソッドの戻り値の型

ストアド プロシージャと関数をドラッグすると**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、生成された戻り値の型<xref:System.Data.Linq.DataContext>方法によって異なりますによっては、項目をドロップする場所です。 項目を既存のエンティティ クラスに直接ドロップするを作成、<xref:System.Data.Linq.DataContext>エンティティ クラスの戻り値の型を持つメソッド以外の項目をドロップの空の領域、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (任意のペイン) では、作成、<xref:System.Data.Linq.DataContext>を返すメソッドを型が自動的に生成されます。 作成される自動生成の型は、ストアド プロシージャ名または関数名に一致する名前と、そのストアド プロシージャまたは関数によって返される各フィールドにマップされるプロパティを持ちます。

> [!NOTE]
> <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、**戻り値の型**プロパティに、**プロパティ**ウィンドウです。 詳細については、次を参照してください。[する方法: DataContext メソッド (O/r デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)です。

データベースから O/R デザイナー画面にドラッグしたオブジェクトには、データベース内のオブジェクトの名前に基づいて自動的に名前が付けられます。 同じオブジェクトを複数回ドラッグすると、新しい名前の末尾に名前を区別する番号が付けられます。 データベース オブジェクト名にスペースや Visual Basic または C# でサポートされない文字が含まれている場合、そのスペースまたは無効な文字はアンダースコアに置き換えられます。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [ストアド プロシージャ](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [チュートリアル : エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)