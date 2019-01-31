---
title: '方法: DataContext メソッドの戻り値の型を変更する (O/R デザイナー)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 297f4df8c34f7289cb39dfaf2b5d1d9c8c88314e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004709"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>方法: DataContext メソッドの戻り値の型を変更する (O/R デザイナー)
戻り値の型を<xref:System.Data.Linq.DataContext>メソッド (ストアド プロシージャまたは関数に基づき作成される) は、ストアド プロシージャを削除またはで関数をする場所によって異なります、 **O/R デザイナー**します。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます (ストアド プロシージャまたは関数によって返されるデータのスキーマがエンティティ クラスの形状と一致する場合)。 空の領域に項目を削除するかどうか、 **O/R デザイナー**、<xref:System.Data.Linq.DataContext>自動的に生成された型を返すメソッドが作成されます。 <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 <xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**[プロパティ]** ウィンドウでメソッドを選択し、**[戻り値の型]** プロパティをクリックします。

> [!NOTE]
>  **[プロパティ]** ウィンドウを使用しても、戻り値の型がエンティティ クラスに設定されている <xref:System.Data.Linq.DataContext> メソッドは、自動生成型を返すようには変更できません。 自動生成型を返すように <xref:System.Data.Linq.DataContext> メソッドを戻すには、元のデータベース オブジェクトをもう一度 **O/R デザイナー**にドラッグする必要があります。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>DataContext メソッドの戻り値の型を、自動生成型からエンティティ クラスに変更するには

1.  メソッド ペインで <xref:System.Data.Linq.DataContext> メソッドを選択します。

2.  **[プロパティ]** ウィンドウの **[戻り値の型]** を選択し、**[戻り値の型]** リストで使用可能なエンティティ クラスを選択します。 一覧で目的のエンティティ クラスでない場合にそれを追加または作成、 **O/R デザイナー**一覧に追加します。

3.  *.dbml* ファイルを保存します。

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>DataContext メソッドの戻り値の型を、エンティティ クラスから自動生成型に変更するには

1.  **メソッド** ペインで <xref:System.Data.Linq.DataContext> メソッドを選択し、削除します。

2.  データベース オブジェクトをドラッグして**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**の空の領域に、 **O/R デザイナー**します。

3.  *.dbml* ファイルを保存します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: ストアド プロシージャや関数にマップされる DataContext メソッドを作成する (O/R デザイナー)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)