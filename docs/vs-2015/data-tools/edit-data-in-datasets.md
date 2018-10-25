---
title: データセットのデータの編集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a983b671b5c6b43009ad3cc32c2cb287977f05c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949293"
---
# <a name="edit-data-in-datasets"></a>データセットのデータの編集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
任意のデータベースのテーブルにデータを編集するのと同様に、データ テーブル内のデータを編集します。 プロセスには、挿入、更新、およびテーブル内のレコードの削除を含めることができます。 データ バインド フォームでは、どのフィールドがユーザーが編集可能なを指定できます。 その場合は、データ バインド インフラストラクチャは、すべての変更の追跡、変更を後で元のデータベースに送信できるようにを処理します。 データにプログラムで編集を行ってそれらの変更をデータベースに送信する場合は、オブジェクトや変更の追跡を行うメソッドを使用する必要があります。  
  
 だけでなく、実際のデータを変更するには、照会することも、<xref:System.Data.DataTable>を特定のデータ行を返します。 たとえば、個々 の行や行 (元および提案された) の特定のバージョン、変更された行のエラーが発生した行のクエリを可能性があります。  
  
## <a name="to-edit-rows-in-a-dataset"></a>データセット内の行を編集するには  
 既存の行を編集する、 <xref:System.Data.DataTable>、検索する必要がある、<xref:System.Data.DataRow>編集、および目的の列に更新された値を割り当てるしたいです。  
  
 編集を使用する行のインデックスがわからない場合、`FindBy`主キーで検索するメソッド。  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 行のインデックスがわかっている場合にアクセスできるし、次のように行を編集します。  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>データセットに新しい行を挿入するには  
 通常、データ バインド コントロールを使用するアプリケーションが使用して新しいレコードを追加、**新規追加**のボタンでは、 [BindingNavigator コントロール](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)します。  
  
 データセットに新しいレコードを手動で追加するには、データ テーブルに、メソッドを呼び出すことによって、新しいデータ行を作成します。 行を追加し、<xref:System.Data.DataRow>コレクション (<xref:System.Data.DataTable.Rows%2A>) の<xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 データセットがデータ ソースに更新を送信する必要がある情報を保持するために使用して、<xref:System.Data.DataRow.Delete%2A>データ テーブルの行を削除するメソッド。 たとえば、アプリケーションは、TableAdapter を使用する場合 (または<xref:System.Data.Common.DataAdapter>)、TableAdapter の`Update`メソッドを持つ、データベース内の行を削除します、<xref:System.Data.DataRow.RowState%2A>の<xref:System.Data.DataRowState>します。  
  
 アプリケーションがデータ ソースに更新を送信する必要がない場合は、データ行のコレクションに直接アクセスするレコードを削除すること (<xref:System.Data.DataRowCollection.Remove%2A>)。  
  
#### <a name="to-delete-records-from-a-data-table"></a>データ テーブルからレコードを削除するには  
  
-   呼び出す、<xref:System.Data.DataRow.Delete%2A>のメソッド、<xref:System.Data.DataRow>します。  
  
     このメソッドは、レコードを物理的に削除されません。 代わりに、削除のレコードをマークします。  
  
    > [!NOTE]
    >  Count プロパティが表示された場合、 <xref:System.Data.DataRowCollection>、結果のカウントには、削除対象としてマークされているレコードが含まれています。 削除対象としてマークされないレコードの正確なカウントを取得する、見てコレクションをループ処理することができます、<xref:System.Data.DataRow.RowState%2A>各レコードのプロパティ。 (削除対象としてマークするレコードが、<xref:System.Data.DataRow.RowState%2A>の<xref:System.Data.DataRowState>)。または、行の状態に基づくフィルターをデータセットのデータ ビューを作成し、そこから、count プロパティを取得することができます。  
  
     次の例を呼び出す方法を示しています、<xref:System.Data.DataRow.Delete%2A>の最初の行をマークするメソッド、`Customers`テーブルの削除済みとして。  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>変更された行があるかを確認します。  
 データセット内のレコードを変更すると、その変更をコミットするまで変更情報が保持されます。 呼び出すと、変更のコミット、`AcceptChanges`メソッドを呼び出すときまたはデータセットまたはデータ テーブルの`Update`TableAdapter またはデータ アダプターのメソッド。  
  
 変更は、各データ行に 2 つの方法を追跡します。  
  
- 各データ行にはそれに関連する情報が含まれています<xref:System.Data.DataRow.RowState%2A>(たとえば、 <xref:System.Data.DataRowState>、 <xref:System.Data.DataRowState>、 <xref:System.Data.DataRowState>、または<xref:System.Data.DataRowState>)。  
  
- 変更されたデータの各行には、その行の複数のバージョンが含まれています (<xref:System.Data.DataRowVersion>)、(前の変更) に、元のバージョンと現在のバージョン (変更後)。 変更が保留中の期間中に (に応答するときに、<xref:System.Data.DataTable.RowChanging>イベント)、3 つ目のバージョン: 提案されたバージョン: も利用できます。 詳細については、次を参照してください。[方法: 特定のバージョンの DataRow を取得](../data-tools/how-to-get-specific-versions-of-a-datarow.md)します。  
  
  データセットが変更された場合、データセットの <xref:System.Data.DataSet.HasChanges%2A> メソッドでは、`true` が返されます。 変更された行が存在することを確認した後は、`GetChanges` または <xref:System.Data.DataSet> の <xref:System.Data.DataTable> メソッドを呼び出して、変更された一連の行を取得できます。 詳細については、次を参照してください。[方法: 変更された行の取得](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)します。  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>行に変更が加えられましたかどうかを判断するには  
  
-   データセットの <xref:System.Data.DataSet.HasChanges%2A> メソッドを呼び出し、変更された行があるかどうかをチェックします。  
  
     次の例からの戻り値を確認する方法を示しています、<xref:System.Data.DataSet.HasChanges%2A>という名前のデータセットに変更された行があるかどうかを検出するためにメソッド`NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>変更の種類を決定します。  
 変更の種類を表示するによって行われたデータセット内の値を渡すことを確認することも、<xref:System.Data.DataRowState>列挙体を<xref:System.Data.DataSet.HasChanges%2A>メソッド。  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>行への変更の種類を確認するには  
  
-   <xref:System.Data.DataRowState> 値を <xref:System.Data.DataSet.HasChanges%2A> メソッドに渡します。  
  
     次の例は、という名前のデータセットを確認する方法を示しています。`NorthwindDataset1`をそれには、新しい行が追加された場合を判断します。  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>エラーが発生した行を探す  
 個々 の列と行のデータを使用する場合は、エラーが発生する可能性があります。 チェックすることができます、`HasErrors`プロパティでエラーが存在するかどうかは確認を<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataRow>します。  
  
1.  チェック、`HasErrors`プロパティをデータセットのすべてのエラーがないかを参照してください。  
  
2.  場合、`HasErrors`プロパティは`true`テーブルのコレクションを反復処理し、エラー行を検索する、行を介してします。  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]

