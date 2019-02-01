---
title: '方法: ストアド プロシージャや関数にマップされる DataContext メソッドを作成する (O-R デザイナー)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ce1d2a4f5e8b068da20d7fd7e46471cdad6d9e59
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952355"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>方法: ストアド プロシージャや関数にマップされる DataContext メソッドを作成する (O/R デザイナー)

ストアド プロシージャと関数を追加することができます、 **O/R デザイナー**として<xref:System.Data.Linq.DataContext>メソッド。 メソッドを呼び出して必要なパラメーターを渡すと、データベースでストアド プロシージャまたは関数が実行され、<xref:System.Data.Linq.DataContext> メソッドの戻り値の型のデータが返されます。 詳細については<xref:System.Data.Linq.DataContext>メソッドを参照してください[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

> [!NOTE]
> 既定値をオーバーライドするストアド プロシージャを使用することもできます[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]実行時の動作を挿入、更新を実行し、データベースに、エンティティ クラスから変更が保存されたときに削除します。 詳細については、「[方法 :更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)」を参照してください。

## <a name="create-datacontext-methods"></a>DataContext メソッドを作成します。

作成することができます<xref:System.Data.Linq.DataContext>メソッドをドラッグしてストアド プロシージャまたは関数から<strong>サーバー エクスプ ローラーまたは * * データベース エクスプ ローラー</strong>上に、 **O/R デザイナー**します。

> [!NOTE]
> 生成された戻り値の型<xref:System.Data.Linq.DataContext>メソッドは、ストアド プロシージャを削除またはで関数をする場所によって異なります、 **O/R デザイナー**します。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。 空の領域に項目をドロップする、 **O/R デザイナー**作成、<xref:System.Data.Linq.DataContext>自動的に生成された型を返すメソッド。 <xref:System.Data.Linq.DataContext> メソッドを **[メソッド]** ペインに追加した後に、その戻り値の型を変更できます。 <xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**[プロパティ]** ウィンドウでメソッドを選択し、**[戻り値の型]** プロパティを調べます。 詳細については、「[方法 :DataContext メソッドの戻り値の型を変更する (O/R デザイナー)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)」を参照してください。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>自動生成された型を返す DataContext メソッドを作成するには

1.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、展開、 **Stored Procedures**作業しているデータベースのノード。

2.  目的のストアド プロシージャの空の領域にドラッグしますを見つけて、 **O/R デザイナー**します。

     自動生成された戻り値の型を使用して <xref:System.Data.Linq.DataContext> メソッドが作成され、**[メソッド]** ペインに表示されます。

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>エンティティ クラスを戻り値の型とする DataContext メソッドを作成するには

1.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、展開、 **Stored Procedures**作業しているデータベースのノード。

2.  目的のストアド プロシージャを見つけて、内の既存のエンティティ クラスをドラッグして、 **O/R デザイナー**します。

     選択したエンティティ クラスを戻り値の型として <xref:System.Data.Linq.DataContext> メソッドが作成され、**[メソッド]** ペインに表示されます。

> [!NOTE]
> 既存の戻り値の型を変更する方法について<xref:System.Data.Linq.DataContext>メソッドを参照してください[方法。DataContext メソッドの戻り値の型を変更する (O/R デザイナー)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [チュートリアル: LINQ to SQL クラスを作成](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic における LINQ の概要](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# での LINQ](/dotnet/csharp/linq/linq-in-csharp)