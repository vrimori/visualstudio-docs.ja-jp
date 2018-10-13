---
title: '方法: データセットの変更をデータベースに保存 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: a197952bcc392f84db3f612a158817237e077d36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202281"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>方法 : データセットの変更をデータベースに保存する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データセット内のデータを変更して検証したら、更新されたデータをデータベースに戻す必要があります。 データベースに変更されたデータを送信するために呼び出す、`Update`のメソッド、 [TableAdapter](../data-tools/tableadapter-overview.md)またはデータ アダプター。 アダプターの `Update` メソッドによって単一のデータ テーブルが更新され、正しいコマンド (INSERT、UPDATE、または DELETE) がテーブル内の各データ行の <xref:System.Data.DataRow.RowState%2A> に基づいて実行されます。  
  
 関連するテーブルのデータを保存する場合、Visual Studio によって TableAdapterManager コンポーネントが作成されます。このコンポーネントは、データベースで定義された外部キー制約に基づく適切な順序で保存を実行するのに役立ちます。 詳細については、次を参照してください。[階層の更新の概要](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)します。  
  
> [!NOTE]
>  アダプターを呼び出すコードを配置する必要がありますので、データセットの内容をデータ ソースを更新しようとすると、エラーが発生することができます、`Update`内のメソッド、 `try` / `catch`ブロックします。  
  
 データ ソースを更新する実際の手順はビジネス ニーズによって異なる場合がありますが、アプリケーションは次の手順に従う必要があります。  
  
1.  内のデータベースに更新を送信しようとするコードを実行する`try` / `catch`ブロックします。  
  
2.  例外が検出された場合は、エラーを引き起こしたデータ行を探します。 詳細については、次を参照してください。[方法: エラーを含む行を見つけます](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)します。  
  
3.  データ行の問題を調整し (可能な場合はプログラムで調整し、可能でない場合は修正のためにユーザーに無効な行を表示する)、もう一度更新してみます (<xref:System.Data.DataRow.HasErrors%2A> プロパティ、<xref:System.Data.DataTable.GetErrors%2A> メソッド)。  
  
## <a name="saving-data-to-a-database"></a>データベースへのデータの保存  
 TableAdapter またはデータ アダプターの `Update` メソッドを呼び出し、データベースに書き込む値があるデータ テーブルの名前を渡します。 データベースに 1 つのデータ テーブルからデータを保存する方法の詳細については、次を参照してください。[チュートリアル: データベース (1 つのテーブル) にデータを保存する](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d)します。  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>TableAdapter を使用してデータベースをデータセットで更新するには  
  
-   囲む、`TableAdapter.Update`メソッド内で、 `try` / `catch`ブロックします。 以下の例は、`Customers` 内の `NorthwindDataSet` テーブルの内容で更新を試みる方法を示します。  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>データ アダプターを使用してデータベースをデータセットで更新するには  
  
-   囲む、`DataAdapter.Update`メソッド内で、 `try` / `catch`ブロックします。 以下の例は、`Table1` 内の `DataSet1` の内容で、データ ソースへの更新を試みる方法を示します。  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>データセットの 2 つの関連テーブルの更新  
 データセットの関連テーブルを更新する場合は、適切な順序で更新し、参照整合性の制約に違反する可能性を小さくする必要があります。 コマンド実行の順序も、データセットの <xref:System.Data.DataRowCollection> のインデックスに従います。 データの整合性エラーが発生しないようにするには、最も適切な方法として、次の順序でデータベースを更新します。  
  
1.  子テーブル : レコードを削除する。  
  
2.  親テーブル : レコードを挿入、更新、および削除する。  
  
3.  子テーブル : レコードを挿入および更新する。  
  
 複数のテーブルからデータを保存する方法の詳細については、次を参照してください。[データベース (複数テーブル) にデータを保存](../data-tools/save-data-to-a-database-multiple-tables.md)します。  
  
 複数の関連するテーブルを更新する場合、トランザクション内にすべての更新ロジックを含める必要があります。 トランザクションは、データベースに対するすべての関連する変更が正常に完了した後に、変更をコミットするプロセスです。 詳細については、「[トランザクションと同時実行](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)します。  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>TableAdapter を使用した 2 つの関連するテーブルの更新  
  
1.  異なるレコードを保持する 3 つの一時 <xref:System.Data.DataTable> を作成します。  
  
2.  呼び出す、`Update`メソッド内からの行の各サブセットに対して、 `try` / `catch`ブロックします。 更新エラーが発生した場合の推奨される処理方法は、エラーを分岐して解決することです。  
  
3.  変更内容をデータセットからデータベースにコミットします。  
  
4.  一時データ テーブルを破棄し、リソースを解放します。  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>データ アダプターを使用した 2 つの関連するテーブルの更新  
  
-   各データ アダプターの `Update` メソッドを呼び出します。  
  
     関連テーブルを含むデータセットによってデータ ソースを更新する方法を次の例に示します。 上の順序に従うために、異なるレコードを保持する 3 つの一時 <xref:System.Data.DataTable> が作成されます。 次に、`Update`内部からの行の各サブセットに対してメソッドが呼び出されます、 `try` / `catch`ブロックします。 更新エラーが発生した場合の推奨される処理方法は、エラーを分岐して解決することです。 続いて、データセットにより変更がコミットされます。 最後に、一時データ テーブルを破棄し、リソースを解放します。  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)