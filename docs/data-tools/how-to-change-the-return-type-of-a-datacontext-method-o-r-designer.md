---
title: '方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089358"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更します。
戻り値の型を<xref:System.Data.Linq.DataContext>メソッド (ストアド プロシージャまたは関数に基づき作成される) は、ストアド プロシージャを削除またはで関数をする場所によって異なります、 **O/R デザイナー**します。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます (ストアド プロシージャまたは関数によって返されるデータのスキーマがエンティティ クラスの形状と一致する場合)。 空の領域に項目を削除するかどうか、 **O/R デザイナー**、<xref:System.Data.Linq.DataContext>自動的に生成された型を返すメソッドが作成されます。 <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 検査または戻り値の型を変更する、<xref:System.Data.Linq.DataContext>メソッドを選択し、クリックして、**戻り値の型**プロパティ、**プロパティ**ウィンドウ。

> [!NOTE]
>  元に戻すことはできません<xref:System.Data.Linq.DataContext>をエンティティ クラスに設定するを使用して、自動生成型を返す戻り値の型を持つメソッド、**プロパティ**ウィンドウ。 元に戻す、<xref:System.Data.Linq.DataContext>メソッドを自動生成された型を返すには、元のデータベース オブジェクトをドラッグする必要があります、 **O/R デザイナー**もう一度。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>DataContext メソッドの戻り値の型を、自動生成型からエンティティ クラスに変更するには

1.  メソッド ペインで <xref:System.Data.Linq.DataContext> メソッドを選択します。

2.  選択**戻り値の型**で、**プロパティ**ウィンドウし、使用可能なエンティティ クラス、**戻り値の型**一覧。 一覧で目的のエンティティ クラスでない場合にそれを追加または作成、 **O/R デザイナー**一覧に追加します。

3.  保存、 *.dbml*ファイル。

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>DataContext メソッドの戻り値の型を、エンティティ クラスから自動生成型に変更するには

1.  選択、<xref:System.Data.Linq.DataContext>メソッドで、**メソッド**ウィンドウして削除します。

2.  データベース オブジェクトをドラッグして**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**の空の領域に、 **O/R デザイナー**します。

3.  保存、 *.dbml*ファイル。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)