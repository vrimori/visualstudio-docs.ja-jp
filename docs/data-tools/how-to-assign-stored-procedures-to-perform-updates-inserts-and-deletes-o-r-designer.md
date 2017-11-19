---
title: "更新を実行するプロシージャを使用して格納が挿入、および Linq to SQL O/R デザイナーで削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f0d6910d2bf449172bac86a3ecd18be8169ef244
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる
ストアド プロシージャは O/R デザイナーに追加でき、通常の <xref:System.Data.Linq.DataContext> メソッドとして実行できます。 既定の上書きを使用することもできます[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]挿入、更新を実行し、変更がエンティティ クラスからデータベースに保存するときに削除するランタイムの動作 (を呼び出すときなど、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>メソッド)。  
  
> [!NOTE]
>  ストアド プロシージャが、クライアントに送信する必要のある値 (たとえば、ストアド プロシージャで計算された値) を返す場合は、ストアド プロシージャに出力パラメーターを作成します。 出力パラメーターを使用できない場合は、O/R デザイナーによって生成されたオーバーライドを利用するのではなく、部分メソッドを実装します。 データベースによって生成される値にマップされるメンバーは、INSERT 操作または UPDATE 操作が正常に完了した後で、適切な値に設定する必要があります。 詳細については、次を参照してください。[をオーバーライドする既定の動作の開発者の責任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)です。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] は、ID 列 (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列であれば、データベースによって生成された値を自動的に処理します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を <xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync>、または <xref:System.Data.Linq.Mapping.AutoSync> のいずれかに設定する必要があります。  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>エンティティ クラスの更新動作の構成  
 既定では、(挿入、更新、および削除)、データベース内のデータに加えられた変更で更新するロジック[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]によってエンティティ クラスが提供される、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]ランタイム。 ランタイムは、既定値に基づく INSERT、UPDATE、および DELETE コマンドを作成します (列と主キー情報) のテーブルのスキーマです。 既定の動作が必要でない場合は、必要な挿入、更新、およびテーブルのデータを操作するために必要な削除を実行するための特定のストアド プロシージャを割り当てることによって、更新動作を構成できます。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 最後に、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>ストアド プロシージャを割り当てて、エンティティ クラスの既定の動作をオーバーライドするには  
  
1.  開く、 **LINQ to SQL**デザイナー内のファイルです。 (で .dbml ファイルをダブルクリックして**ソリューション エクスプ ローラー**)。  
  
2.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、展開**Stored Procedures** insert、Update を使用するストアド プロシージャを探しますまたは、エンティティ クラスのコマンドを削除します。  
  
3.  ストアド プロシージャを O/R デザイナーにドラッグします。  
  
     ストアド プロシージャが <xref:System.Data.Linq.DataContext> メソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。  
  
4.  更新の実行にストアド プロシージャを使用するエンティティ クラスを選択します。  
  
5.  **プロパティ**ウィンドウで、オーバーライドするコマンドを選択 (**挿入**、**更新**、または**削除**)。  
  
6.  単語の横にある省略記号 (...) をクリックして**ランタイムを使用**を開くには、**動作の構成** ダイアログ ボックス。  
  
7.  選択**カスタマイズ**です。  
  
8.  目的のストアド プロシージャを選択して、**カスタマイズ** ボックスの一覧です。  
  
9. 一覧を調べる**メソッド引数**と**クラス プロパティ**ことを確認する、**メソッド引数**を適切なマップ**のクラスのプロパティ**. マップ元のメソッド引数 (original _*ArgumentName*) を元のプロパティ (*PropertyName* (オリジナル)) Update および Delete コマンドについてです。  
  
    > [!NOTE]
    >  既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 変更されたプロパティ名がテーブルとエンティティ クラス間で一致しなくなり、デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。  
  
10. をクリックして**OK**または**適用**です。  
  
    > [!NOTE]
    >  をクリックする限り、各クラスと動作の組み合わせに対して動作の構成を続行できます**適用**各変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**変更を適用する機会が表示され、警告ダイアログ ボックス。  
  
更新プログラムの既定のランタイム ロジックを使用するように戻すには、Insert、Update、隣の省略記号をクリックするか、コマンドを削除、**プロパティ**クリックしてウィンドウ**ランタイムを使用して**で、 **動作を構成する** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目
[Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[DataContext メソッド](../data-tools/datacontext-methods-o-r-designer.md)   
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)   
[Insert、Update、および削除の操作 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)