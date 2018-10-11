---
title: '方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 802627f59f54b9a4b1179ba5c643b4671f4f7ce0
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878955"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](https://docs.microsoft.com/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)します。  
  
  
ストアド プロシージャは O/R デザイナーに追加でき、通常の <xref:System.Data.Linq.DataContext> メソッドとして実行できます。 既定値も使用[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]実行時の動作を挿入、更新を実行し、データベースに、エンティティ クラスから変更が保存されたときに削除します (などを呼び出すときに、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>メソッド)。  
  
> [!NOTE]
>  ストアド プロシージャが、クライアントに送信する必要のある値 (たとえば、ストアド プロシージャで計算された値) を返す場合は、ストアド プロシージャに出力パラメーターを作成します。 出力パラメーターを使用できない場合は、O/R デザイナーによって生成されたオーバーライドを利用するのではなく、部分メソッドを実装します。 データベースによって生成される値にマップされるメンバーは、INSERT 操作または UPDATE 操作が正常に完了した後で、適切な値に設定する必要があります。 詳細については、次を参照してください。[開発者でオーバーライドする既定の動作の責任](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1)します。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] は、ID 列 (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列であれば、データベースによって生成された値を自動的に処理します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を <xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync>、または <xref:System.Data.Linq.Mapping.AutoSync> のいずれかに設定する必要があります。  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>エンティティ クラスの更新動作の構成  
 既定では、[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] エンティティ クラスのデータに対して行われた変更でデータベースを更新 (挿入、更新、および削除) するロジックは、[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ランタイムによって提供されます。 ランタイムは、既定値 (列と主キー情報) のテーブルのスキーマに基づく Insert、Update、および Delete コマンドを作成します。 既定の動作が望ましくないと、更新動作を構成するには、必要な挿入、更新を実行するための特定のストアド プロシージャを割り当てることで、テーブルのデータを操作するために必要な削除。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 最後に、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>ストアド プロシージャを割り当てて、エンティティ クラスの既定の動作をオーバーライドするには  
  
1.  開く、 **LINQ to SQL**デザイナー内のファイル。 (で .dbml ファイルをダブルクリック**ソリューション エクスプ ローラー**)。  
  
2.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、展開**Stored Procedures** Insert、Update を使用するストアド プロシージャを探しますまたは、エンティティ クラスのコマンドを削除します。  
  
3.  ストアド プロシージャを O/R デザイナーにドラッグします。  
  
     ストアド プロシージャが <xref:System.Data.Linq.DataContext> メソッドとしてメソッド ペインに追加されます。 詳細については [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md) を参照してください。  
  
4.  更新の実行にストアド プロシージャを使用するエンティティ クラスを選択します。  
  
5.  **プロパティ**ウィンドウで、オーバーライドするコマンドを選択します (**挿入**、 **Update**、または**削除**)。  
  
6.  単語の横にある省略記号 (...) をクリックします。**ランタイムを使用**を開く、**動作の構成** ダイアログ ボックス。  
  
7.  選択**カスタマイズ**します。  
  
8.  目的のストアド プロシージャの選択、**カスタマイズ**一覧。  
  
9. 一覧を調べて**メソッド引数**と**クラス プロパティ**ことを確認する、**メソッド引数**を適切なマップ**クラスのプロパティ**. マップ元のメソッド引数 (original _*ArgumentName*) を元のプロパティ (*PropertyName* (オリジナル)) の Update および Delete コマンド。  
  
    > [!NOTE]
    >  既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 変更されたプロパティ名がテーブルとエンティティ クラス間で一致しなくなり、デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。  
  
10. クリックして**OK**または**適用**します。  
  
    > [!NOTE]
    >  クリックすると、各クラスと動作の組み合わせの動作を構成を続行できます**適用**それぞれの変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**、警告ダイアログ ボックスを提供するすべての変更を適用する機会が表示されます。  
  
     既定のランタイム ロジックを使用して、更新に戻すには、Insert、Update、横にある省略記号をクリックしてまたは Delete コマンドで、**プロパティ**クリックしてウィンドウ**ランタイムを使用して、** で、 **動作を構成する** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [チュートリアル: Northwind の Customers テーブル ストアド プロシージャを更新プログラムを作成します。](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [挿入、更新、および削除の各操作](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

