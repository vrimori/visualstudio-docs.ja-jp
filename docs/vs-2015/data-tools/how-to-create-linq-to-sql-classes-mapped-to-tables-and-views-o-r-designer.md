---
title: '方法: LINQ to SQL クラスのテーブルとビュー (O/R デザイナー) にマップを作成 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d9cebc980b62a5676ee4e65e5554086a273fa73
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535962"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>方法: LINQ to SQL クラスのテーブルとビュー (O/R デザイナー) にマップを作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: LINQ to SQL クラスのテーブルとビュー (O/R デザイナー) にマップに作成](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer)です。

LINQ to SQL クラス データベース テーブルおよびビューにマップされているといいます*エンティティ クラス*します。 エンティティ クラスはレコードにマップされますが、エンティティ クラスの個々のプロパティはレコードを構成する個々の列にマップされます。 テーブルまたはビューをドラッグしてデータベース テーブルまたはビューに基づくエンティティ クラスを作成**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [LINQ to SQL ツールVisual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)します。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]クラスを生成し、特定の適用 [!SQL の属性に LINQ を有効にする [です。SQL 機能を LINQ (データ通信編集および編集の機能、 <xref:System.Data.Linq.DataContext>)。 詳細については [!LINQ to SQL クラスを参照してください[LINQ to SQL オブジェクト モデル](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)します。

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]簡単なオブジェクト リレーショナル マッパーは、1 対 1 のマッピング関係のみをサポートしているためです。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 1 つのエンティティ クラスを複数のテーブルにマップするなど、複雑なマッピングはサポートされていません。 ただし、複数の関連テーブルを結合するビューにエンティティ クラスをマップすることはできます。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスの作成
 テーブルまたはビューからドラッグ**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]に加え、エンティティ クラスを作成、<xref:System.Data.Linq.DataContext>に使用されるメソッド更新プログラムを実行しています。

 既定で、[!LINQ to SQL ランタイムは、更新可能なエンティティ クラスからデータベースに変更を保存するためのロジックを作成します。 このロジックは、テーブルのスキーマ (列定義と主キー情報) に基づいています。 ストアド プロシージャを使用して、挿入、更新を実行するエンティティ クラスを構成することができ、削除します既定値を使用する代わりにこの動作をしない場合は [!。LINQ to SQL ランタイムの動作です。 詳細については、次を参照してください。[方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>データベース テーブルまたはビューにマップされる LINQ to SQL クラスを作成するには

1.  **Server**/**データベース エクスプ ローラー**、展開**テーブル**または**ビュー**とデータベースのテーブルを検索または表示します。アプリケーションで使用します。

2.  テーブルまたはビューを [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]にドラッグします。

     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。 このエンティティ クラスには、選択されたテーブルまたはビューの列にマップされるプロパティが含まれています。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>オブジェクト データ ソースの作成とフォームへのデータの表示
 使用してエンティティ クラスを作成した後、 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]、オブジェクト データ ソースを作成して設定できる、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)エンティティ クラスを使用します。

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL エンティティ クラスに基づいてオブジェクト データ ソースを作成するには

1.  **ビルド** メニューのをクリックして**ソリューションのビルド**プロジェクトをビルドします。

2.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

3.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

4.  をクリックして**オブジェクト**で、**データ ソースの種類を選択**ページをクリックして**次**。

5.  ノードを展開し、クラスを探して選択します。

    > [!NOTE]
    > 場合、**顧客**クラスは使用できません、ウィザードをキャンセル、プロジェクトをビルド、およびウィザードを再度実行します。

6.  をクリックして**完了**、データ ソースを作成し、追加、**顧客**エンティティ クラスを**データ ソース**ウィンドウ。

7.  項目をドラッグ、**データソース**ウィンドウからフォームにします。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: ストアド プロシージャや関数にマップされる DataContext メソッドを作成する (O/R デザイナー)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL オブジェクト モデル](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [チュートリアル : エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [チュートリアル: エンティティ クラスに検証を追加します。](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [方法: LINQ to SQL クラス間の関連付け (リレーションシップ) を作成する (O/R デザイナー)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)