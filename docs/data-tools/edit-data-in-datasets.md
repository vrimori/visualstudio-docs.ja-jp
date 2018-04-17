---
title: データセット内のデータを編集 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a72949ad06b9140faa3e5013a8fd07e98b4db172
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="edit-data-in-datasets"></a>データセット内のデータを編集します。
任意のデータベース内のテーブル内のデータを編集するのと同様に、データ テーブル内のデータを編集します。 挿入、更新、およびテーブル内のレコードを削除すると、プロセスを含めることができます。 データ バインド フォームでは、どのフィールドがユーザーが編集できるを指定できます。 このような場合では、データ バインド インフラストラクチャは、すべての変更の追跡、変更を後で、データベースに送信できるようにを処理します。 プログラムによって、データへの編集を行うし、それらの変更をデータベースに送信する場合、オブジェクトや変更の追跡を自動的に行うメソッドを使用する必要があります。  
  
だけでなく、実際のデータを変更するには、照会することも、<xref:System.Data.DataTable>を特定のデータ行を返します。 たとえば、個々 の行、特定のバージョン (元と提案された) 行の変更された行または行のエラーが発生したクエリを可能性があります。  
  
## <a name="to-edit-rows-in-a-dataset"></a>データセット内の行を編集するには  
既存の行を編集する、<xref:System.Data.DataTable>を検索する必要があります、<xref:System.Data.DataRow>を編集、および目的の列に、更新された値を割り当てる場合します。  
  
編集を使用する、行のインデックスを理解していない場合、`FindBy`主キーによって検索します。  
  
[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]  
  
行のインデックスがわかっている場合にアクセスできるし、行を次のように編集します。  
  
[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>データセットに新しい行を挿入するには  
通常のデータ バインド コントロールを使用するアプリケーションが使用して新しいレコードを追加、**新規追加**のボタンでは、 [BindingNavigator コントロール](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)です。  
  
データセットに新しいレコードを手動で追加するには、DataTable でメソッドを呼び出すことにより、新しいデータ行を作成します。 行を追加、<xref:System.Data.DataRow>コレクション (<xref:System.Data.DataTable.Rows%2A>) の<xref:System.Data.DataTable>:  
  
[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]  
  
更新を送信するデータ ソースにデータセットが必要な情報を保持するために使用して、<xref:System.Data.DataRow.Delete%2A>データ テーブルの行を削除する方法です。 たとえば、アプリケーションは、TableAdapter を使用する場合 (または<xref:System.Data.Common.DataAdapter>)、TableAdapter の`Update`メソッドを持つ、データベース内の行の削除、<xref:System.Data.DataRow.RowState%2A>の<xref:System.Data.DataRowState.Deleted>です。  
  
アプリケーションは、データ ソースに更新を送信する必要はありません場合はによりデータ行のコレクションに直接アクセスするレコードを削除すること (<xref:System.Data.DataRowCollection.Remove%2A>)。  
  
#### <a name="to-delete-records-from-a-data-table"></a>データ テーブルからレコードを削除するには  
  
-   呼び出す、<xref:System.Data.DataRow.Delete%2A>のメソッド、<xref:System.Data.DataRow>です。  
  
     このメソッドは、レコードを物理的に削除されません。 代わりに、レコードを削除対象をマークします。  
  
    > [!NOTE]
    >  Count プロパティを取得する場合、 <xref:System.Data.DataRowCollection>、結果のカウントには、削除対象としてマークされているレコードが含まれています。 削除対象としてマークされないレコードの正確なカウントを取得する、コレクションをループできます、<xref:System.Data.DataRow.RowState%2A>各レコードのプロパティです。 (レコードの削除対象としてマークがある、<xref:System.Data.DataRow.RowState%2A>の<xref:System.Data.DataRowState.Deleted>)。代わりに、行の状態に基づくフィルターをデータセットのデータ ビューを作成したり、そこから、count プロパティを取得します。  
  
次の例を呼び出す方法を示します、<xref:System.Data.DataRow.Delete%2A>の最初の行をマークするメソッド、`Customers`テーブルの削除済みとして。  
  
[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]  
  
## <a name="determine-if-there-are-changed-rows"></a>変更された行があるかを確認します。  
データセット内のレコードを変更すると、その変更をコミットするまで変更情報が保持されます。 呼び出すときに、変更をコミットする、`AcceptChanges`メソッドを呼び出すときまたはデータセットまたはデータのテーブルの`Update`TableAdapter またはデータ アダプターのメソッドです。  
  
各データ行で追跡対象の 2 つの方法を変更には。  
  
-   各データ行には、関連する情報が含まれています。 その<xref:System.Data.DataRow.RowState%2A>(たとえば、 <xref:System.Data.DataRowState.Added>、 <xref:System.Data.DataRowState.Modified>、 <xref:System.Data.DataRowState.Deleted>、または<xref:System.Data.DataRowState.Unchanged>)。  
  
-   変更されたデータの各行には、その行の複数のバージョンが含まれています (<xref:System.Data.DataRowVersion>)、元のバージョン (変更前) に、と現在のバージョン (変更後)。 変更が保留中の期間中に (に応答するときに、<xref:System.Data.DataTable.RowChanging>イベント)、3 つ目のバージョン: 提案されたバージョン — も利用できます。 
  
データセットが変更された場合、データセットの <xref:System.Data.DataSet.HasChanges%2A> メソッドでは、`true` が返されます。 変更された行が存在することを確認した後は、`GetChanges` または <xref:System.Data.DataSet> の <xref:System.Data.DataTable> メソッドを呼び出して、変更された一連の行を取得できます。   
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>すべての行に変更が加えられたかどうかを決定するには  
  
-   データセットの <xref:System.Data.DataSet.HasChanges%2A> メソッドを呼び出し、変更された行があるかどうかをチェックします。  
  
次の例からの戻り値を確認する方法を示しています、<xref:System.Data.DataSet.HasChanges%2A>という名前のデータセットに変更された行があるかどうかを検出するためにメソッド`NorthwindDataset1`:  
  
[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]  
  
## <a name="determine-the-type-of-changes"></a>変更の種類を決定します。  
変更の種類を表示するで行われたデータセット内の値を渡すことを確認することも、<xref:System.Data.DataRowState>列挙型を<xref:System.Data.DataSet.HasChanges%2A>メソッドです。  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>行への変更の種類を確認するには  
  
-   <xref:System.Data.DataRowState> 値を <xref:System.Data.DataSet.HasChanges%2A> メソッドに渡します。  
  
次の例は、という名前のデータセットを確認する方法を示しています。`NorthwindDataset1`をそれに、新しい行が追加されている場合を判断します。  
  
[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]  
  
## <a name="to-locate-rows-that-have-errors"></a>エラーが発生した行を探す  
個々 の列と行のデータを処理するときは、エラーが発生する可能性があります。 チェックすることができます、`HasErrors`のかどうかにエラーが存在するかを決定するプロパティ、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataRow>です。  
  
1.  チェック、`HasErrors`プロパティをデータセット内のエラーがあるかどうかを参照してください。  
  
2.  場合、`HasErrors`プロパティは`true`テーブルのコレクションを反復処理し、エラーを含む行を検索する、行を介して。  

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>関連項目
[Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)