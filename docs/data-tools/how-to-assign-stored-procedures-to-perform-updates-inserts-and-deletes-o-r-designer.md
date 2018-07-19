---
title: 更新を実行するプロシージャを格納されている使用の挿入、および Linq to SQL O/R デザイナーでの削除
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089777"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる

ストアド プロシージャに追加できる、 **O/R デザイナー**され、通常どおり実行<xref:System.Data.Linq.DataContext>メソッド。 LINQ to SQL ランタイムの動作を挿入、更新を実行し、変更をエンティティ クラスからデータベースに保存するときに削除の既定をオーバーライドするも使用 (たとえば、呼び出し時に、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>メソッド)。

> [!NOTE]
> ストアド プロシージャが、クライアントに送信する必要のある値 (たとえば、ストアド プロシージャで計算された値) を返す場合は、ストアド プロシージャに出力パラメーターを作成します。 出力パラメーターを使用できない場合は、O/R デザイナーによって生成されたオーバーライドを利用するのではなく、部分メソッドを実装します。 データベースによって生成される値にマップされるメンバーは、INSERT 操作または UPDATE 操作が正常に完了した後で、適切な値に設定する必要があります。 詳細については、次を参照してください。[開発者でオーバーライドする既定の動作の責任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)します。

> [!NOTE]
> LINQ to SQL では、identity (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列を自動的にデータベースによって生成された値を処理します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースによって生成された値を返す必要があります手動で設定する<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>に**true**と<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>、次のいずれか: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)、 [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)、または[AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)します。

## <a name="configure-the-update-behavior-of-an-entity-class"></a>エンティティ クラスの更新プログラムの動作を構成します。

既定では、LINQ to SQL エンティティ クラスのデータに加えられた変更 (挿入、更新、および削除) のデータベースを更新するロジックは、LINQ to SQL ランタイムによって提供されます。 ランタイムは、既定値 (列と主キー情報) のテーブルのスキーマに基づく INSERT、UPDATE、および DELETE コマンドを作成します。 既定の動作が望ましくない場合は、必要な挿入、更新、およびテーブルのデータを操作するために必要な削除を実行するための特定のストアド プロシージャを割り当てることで、更新動作を構成できます。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 最後に、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>ストアド プロシージャを割り当てて、エンティティ クラスの既定の動作をオーバーライドするには

1.  開く、 **LINQ to SQL**デザイナー内のファイル。 (ダブルクリックして、 **.dbml**ファイル**ソリューション エクスプ ローラー**)。

2.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、展開**Stored Procedures**探しストアド プロシージャを使用して、insert、Update、または削除します。エンティティ クラスのコマンド。

3.  ストアド プロシージャをドラッグして、 **O/R デザイナー**します。

     ストアド プロシージャが <xref:System.Data.Linq.DataContext> メソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

4.  更新の実行にストアド プロシージャを使用するエンティティ クラスを選択します。

5.  **プロパティ**ウィンドウで、オーバーライドするコマンドを選択します (**挿入**、 **Update**、または**削除**)。

6.  単語の横にある省略記号 (...) をクリックします。**ランタイムを使用**を開く、**動作の構成** ダイアログ ボックス。

7.  選択**カスタマイズ**します。

8.  目的のストアド プロシージャの選択、**カスタマイズ**一覧。

9. 一覧を調べて**メソッド引数**と**クラス プロパティ**ことを確認する、**メソッド引数**を適切なマップ**クラスのプロパティ**. マップ元のメソッド引数 (`Original_<ArgumentName>`) を元のプロパティ (`<PropertyName> (Original)`) の`Update`と`Delete`コマンド。

    > [!NOTE]
    > 既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 変更されたプロパティ名がテーブルとエンティティ クラス間で一致しなくなり、デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。

10. クリックして**OK**または**適用**します。

    > [!NOTE]
    >  クリックすると、クラスと動作の組み合わせごとの動作を構成を続行できます**適用**それぞれの変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**、警告ダイアログ ボックスが表示され、変更を適用する機会を提供します。

、既定のランタイム ロジックを使用して、の更新に戻すに場合は、横にある省略記号をクリックして、**挿入**、 **Update**、または**削除**コマンド、**プロパティ**クリックしてウィンドウ**ランタイムを使用して、** で、**動作の構成** ダイアログ ボックス。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext メソッド](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [挿入、更新、および削除操作 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)