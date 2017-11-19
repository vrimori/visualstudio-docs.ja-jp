---
title: "方法: LINQ to SQL クラス テーブルとビュー (O R デザイナー) にマップを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 318acd282090dd17fcfd7fd12e7370e906c67806
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>方法: LINQ to SQL クラス テーブルとビュー (O/R デザイナー) にマップを作成
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]データベースのテーブルとビューにマップされているクラスと呼ばれます*エンティティ クラス*です。 エンティティ クラスはレコードにマップされますが、エンティティ クラスの個々のプロパティはレコードを構成する個々の列にマップされます。 テーブルまたはビューをドラッグすることによりデータベース テーブルまたはビューに基づくエンティティ クラスを作成する**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [LINQ to SQL ツールVisual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)です。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]クラスを生成し、固有の仕様を適用[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]を有効にする属性[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]機能 (データ通信編集および編集の機能、 <xref:System.Data.Linq.DataContext>)。 詳細については[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]クラスを参照してください[LINQ to SQL オブジェクト モデル](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)です。  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]単純なオブジェクト リレーショナル マッパーでは 1:1 のマッピング関係のみをサポートします。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 1 つのエンティティ クラスを複数のテーブルにマップするなど、複雑なマッピングはサポートされていません。 ただし、複数の関連テーブルを結合するビューにエンティティ クラスをマップすることはできます。  
  
## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスの作成  
 ドラッグからテーブルまたはビュー**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]他に、エンティティ クラスを作成、<xref:System.Data.Linq.DataContext>の使用方法更新プログラムを実行しています。  
  
 既定では、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムによって、更新可能なエンティティ クラスの変更をデータベースに保存するロジックが作成されます。 このロジックは、テーブルのスキーマ (列定義と主キー情報) に基づいています。 この動作が不要な場合は、既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作の代わりに、ストアド プロシージャを使用して挿入、更新、および削除を実行するようにエンティティ クラスを構成できます。 詳細については、次を参照してください。[する方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)です。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスを作成するには  
  
1.  **サーバー**/**データベース エクスプ ローラー**、展開**テーブル**または**ビュー**とデータベースのテーブルを検索または表示します。アプリケーションで使用します。  
  
2.  テーブルまたはビューを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。  
  
     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。 このエンティティ クラスには、選択されたテーブルまたはビューの列にマップされるプロパティが含まれています。  
  
## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>オブジェクト データ ソースの作成とフォームへのデータの表示  
 使用してエンティティ クラスを作成した後、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、オブジェクト データ ソースを作成して設定、[データ ソース ウィンドウ](add-new-data-sources.md)エンティティ クラスを使用します。  
  
#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL エンティティ クラスに基づいてオブジェクト データ ソースを作成するには  
  
1.  **ビルド** メニューのをクリックして**ソリューションのビルド**プロジェクトをビルドします。  
  
2.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]**をクリックします。  
  
4.  をクリックして**オブジェクト**上、**データ ソースの種類を選択**ページし、をクリックして**[次へ]**です。  
  
5.  ノードを展開し、クラスを探して選択します。  
  
    > [!NOTE]
    >  場合、**顧客**クラスは使用できません、ウィザードをキャンセル、プロジェクトをビルド、およびウィザードを再度実行します。  
  
6.  をクリックして**完了**データ ソースを作成し、追加、**顧客**エンティティ クラスを**データ ソース**ウィンドウです。  
  
7.  項目をドラッグ、**データソース**ウィンドウからフォームにします。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL オブジェクト モデル](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)   
 [チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
  [方法: LINQ to SQL クラス (O/R デザイナー) の間の関連付け (リレーションシップ) を作成します。](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)