---
title: '方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ae5fb4b3785bde0e092f68b62a9b030069a52aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942700"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成

ストアド プロシージャと関数を追加することができます、 **O/R デザイナー**として<xref:System.Data.Linq.DataContext>メソッド。 メソッドを呼び出すと、必要なパラメーターを渡すこと、データベースでストアド プロシージャまたは関数を実行し、戻り値の型のデータを返します、<xref:System.Data.Linq.DataContext>メソッド。 詳細については<xref:System.Data.Linq.DataContext>メソッドを参照してください[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

> [!NOTE]
> 既定値をオーバーライドするストアド プロシージャを使用することもできます[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]実行時の動作を挿入、更新を実行し、データベースに、エンティティ クラスから変更が保存されたときに削除します。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。

## <a name="create-datacontext-methods"></a>DataContext メソッドを作成します。

作成することができます<xref:System.Data.Linq.DataContext>メソッドをドラッグしてストアド プロシージャまたは関数から<strong>サーバー エクスプ ローラーまたは * * データベース エクスプ ローラー</strong>上に、 **O/R デザイナー**します。

> [!NOTE]
> 生成された戻り値の型<xref:System.Data.Linq.DataContext>メソッドは、ストアド プロシージャを削除またはで関数をする場所によって異なります、 **O/R デザイナー**します。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。 空の領域に項目をドロップする、 **O/R デザイナー**作成、<xref:System.Data.Linq.DataContext>自動的に生成された型を返すメソッド。 戻り値の型を変更することができます、<xref:System.Data.Linq.DataContext>メソッドに追加した後、**メソッド**ウィンドウ。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、検査、**戻り値の型**プロパティ、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[方法: DataContext メソッド (O/r デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>自動生成された型を返す DataContext メソッドを作成するには

1.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、展開、 **Stored Procedures**作業しているデータベースのノード。

2.  目的のストアド プロシージャの空の領域にドラッグしますを見つけて、 **O/R デザイナー**します。

     <xref:System.Data.Linq.DataContext>メソッドが自動的に生成された戻り値の型で作成され、**メソッド**ウィンドウ。

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>エンティティ クラスを戻り値の型とする DataContext メソッドを作成するには

1.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、展開、 **Stored Procedures**作業しているデータベースのノード。

2.  目的のストアド プロシージャを見つけて、内の既存のエンティティ クラスをドラッグして、 **O/R デザイナー**します。

     <xref:System.Data.Linq.DataContext>メソッドが、選択したエンティティ クラスの戻り値の型で作成され、**メソッド**ウィンドウ。

> [!NOTE]
> 既存の戻り値の型を変更する方法について<xref:System.Data.Linq.DataContext>メソッドを参照してください[方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更する](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)します。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [チュートリアル: LINQ to SQL クラスを作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic における LINQ の概要](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# での LINQ](/dotnet/csharp/linq/linq-in-csharp)