---
title: 更新を実行するプロシージャを格納されている使用の挿入、および Linq to SQL O/R デザイナーでの削除
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 96db9d95eeeb21ad890e12e2a05d5313cb426796
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949416"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)

ストアド プロシージャは **O/R デザイナー**に追加でき、通常の <xref:System.Data.Linq.DataContext> メソッドとして実行できます。 LINQ to SQL ランタイムの動作を挿入、更新を実行し、変更をエンティティ クラスからデータベースに保存するときに削除の既定をオーバーライドするも使用 (たとえば、呼び出し時に、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>メソッド)。

> [!NOTE]
> ストアド プロシージャが、クライアントに送信する必要のある値 (たとえば、ストアド プロシージャで計算された値) を返す場合は、ストアド プロシージャに出力パラメーターを作成します。 出力パラメーターを使用できない場合は、O/R デザイナーによって生成されたオーバーライドを利用するのではなく、部分メソッドを実装します。 データベースによって生成される値にマップされるメンバーは、INSERT 操作または UPDATE 操作が正常に完了した後で、適切な値に設定する必要があります。 詳細については、次を参照してください。[開発者でオーバーライドする既定の動作の責任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)します。

> [!NOTE]
> LINQ to SQL では、identity (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列を自動的にデータベースによって生成された値を処理します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースによって生成された値を返す必要があります手動で設定する<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>に**true**と<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>次のいずれか。[AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)、 [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)、または[AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)します。

## <a name="configure-the-update-behavior-of-an-entity-class"></a>エンティティ クラスの更新プログラムの動作を構成します。

既定では、LINQ to SQL エンティティ クラスのデータに加えられた変更 (挿入、更新、および削除) のデータベースを更新するロジックは、LINQ to SQL ランタイムによって提供されます。 ランタイムは、テーブルのスキーマ (列および主キー情報) に基づいて、既定の INSERT、UPDATE、および DELETE の各コマンドを作成します。 既定の動作が望ましくない場合は、必要な挿入、更新、およびテーブルのデータを操作するために必要な削除を実行するための特定のストアド プロシージャを割り当てることで、更新動作を構成できます。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 最後に、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>ストアド プロシージャを割り当てて、エンティティ クラスの既定の動作をオーバーライドするには

1.  デザイナーで **LINQ to SQL** ファイルを開きます。 (**ソリューション エクスプローラー**で **.dbml** ファイルをダブルクリックします。)

2.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、**[ストアド プロシージャ]** を展開し、エンティティ クラスの Insert、Update、Delete の各コマンドで使用するストアド プロシージャを探します。

3.  ストアド プロシージャを **O/R デザイナー**にドラッグします。

     ストアド プロシージャが <xref:System.Data.Linq.DataContext> メソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

4.  更新の実行にストアド プロシージャを使用するエンティティ クラスを選択します。

5.  **[プロパティ]** ウィンドウで、オーバーライドするコマンド (**[Insert]**、**[Update]**、または **[Delete]**) を選択します。

6.  **[ランタイムを使用]** の横にある省略記号 ([...]) をクリックして、**[動作の構成]** ダイアログ ボックスを開きます。

7.  **[カスタマイズ]** を選択します。

8.  **[カスタマイズ]** リストで、目的のストアド プロシージャを選択します。

9. **[メソッドの引数]** および **[クラスのプロパティ]** のリストを調べて、**[メソッドの引数]** が適切な **[クラスのプロパティ]** にマップされていることを確認します。 マップ元のメソッド引数 (`Original_<ArgumentName>`) を元のプロパティ (`<PropertyName> (Original)`) の`Update`と`Delete`コマンド。

    > [!NOTE]
    > 既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 変更されたプロパティ名がテーブルとエンティティ クラス間で一致しなくなり、デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。

10. **[OK]** または **[適用]** をクリックします。

    > [!NOTE]
    >  クリックすると、クラスと動作の組み合わせごとの動作を構成を続行できます**適用**それぞれの変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**、警告ダイアログ ボックスが表示され、変更を適用する機会を提供します。

更新時に既定のランタイム ロジックを使用するように戻すには、**[プロパティ]** ウィンドウで、**[Insert]**、**[Update]**、または **[Delete]** の各コマンドの横にある省略記号をクリックし、**[動作の構成]** ダイアログ ボックスで **[ランタイムを使用]** を選択します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext メソッド](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [挿入、更新、および削除操作 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)