---
title: データセット内のデータの検証 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a85e7b429300ce86290e707bb612d778b8fbb20e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="validate-data-in-datasets"></a>データセット内のデータを検証します。
データの検証は、データ オブジェクトに入力されている値がデータセットのスキーマ内の制約に従っていることを確認するプロセスです。 検証プロセスはまた、これらの値がアプリケーション用に設定されている規則に従っていることを確認します。 更新プログラムを基になるデータベースに送信する前にデータを検証することをお勧めします。 これにより、エラーだけでなく、アプリケーションとデータベース間のラウンド トリップの潜在的な数が減少します。  
  
データセットに書き込まれたデータがデータセット自体に検証を組み込むことによって有効であるを確認することができます。 データセットは、更新プログラムの実行方法に関係なくデータをチェックできる — コントロールをフォームでは、コンポーネント内またはその他の方法で直接かどうか。 データセットは、アプリケーションとは異なり、データベース バックエンド) の一部であるため、アプリケーション固有の検証をビルドする論理的な場所であります。  
  
データセットの部分クラス ファイルは、アプリケーションに検証を追加する最適な場所です。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]を開き、**データセット デザイナー**検証を作成する列またはテーブルをダブルクリックします。 この操作は自動的に作成、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>イベント ハンドラー。 
  
## <a name="validate-data"></a>データを検証します。  
 次の方法では、データセット内での検証を実行できます。  
  
-   アプリケーション固有の検証を作成することでは、個々 のデータ列の値を変更するときを確認できます。  詳細については、次を参照してください。[する方法: 列変更中にデータを検証](validate-data-in-datasets.md)です。  
  
-   全体のデータ値にデータをチェックできるアプリケーション固有の検証を作成することで、行が変更されます。 詳細については、次を参照してください。[する方法: 行変更中にデータを検証](validate-data-in-datasets.md)です。  
  
-   データセットの実際のスキーマ定義の一部としてにキー、一意の制約を作成します。 
  
-   プロパティを設定して、<xref:System.Data.DataColumn>オブジェクトのように<xref:System.Data.DataColumn.MaxLength%2A>、 <xref:System.Data.DataColumn.AllowDBNull%2A>、および<xref:System.Data.DataColumn.Unique%2A>です。  
  
いくつかのイベントはによって発生させ、<xref:System.Data.DataTable>オブジェクト レコードで変更が発生しているとき。  
  
-   <xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.ColumnChanged>中に、個々 の列を変更するたびにイベントが発生します。 <xref:System.Data.DataTable.ColumnChanging>イベントは、特定の列に変更を検証する場合に便利です。 提案された変更に関する情報は、イベントの引数として渡されます。 
-   <xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>中に、いずれかの後のイベントが発生する行の変更。 <xref:System.Data.DataTable.RowChanging>イベントは一般的なです。 これは、行で、変更がどこかに発生しているが、どの列が変更されたかわからないことを示します。  
  
既定では、列にそれぞれの変更では、4 つのイベントがそのためを生成します。 1 つは、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.ColumnChanged>変更されている特定の列のイベントです。 次に、<xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>イベント。 行に複数の変更が出されている場合は、それぞれの変更イベントが生成されます。  
  
> [!NOTE]
>  データ行の<xref:System.Data.DataRow.BeginEdit%2A>メソッドがオフに、<xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>それぞれ個々 の列の変更後のイベントです。 その場合は、イベントをまで発生しません、<xref:System.Data.DataRow.EndEdit%2A>メソッドが呼び出されて、ときに、<xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>イベントが 1 回だけ発生します。 詳細については、次を参照してください。[データセットの読み込み中に制約をオフに](../data-tools/turn-off-constraints-while-filling-a-dataset.md)です。  
  
イベントの選択は、どのように細分化して、検証するによって異なります。 列が変更されたときすぐには、エラーをキャッチすることが重要である場合を使用して検証をビルド、<xref:System.Data.DataTable.ColumnChanging>イベント。 それ以外の場合を使用して、<xref:System.Data.DataTable.RowChanging>イベントで、一度にいくつかのエラーをキャッチする可能性があります。 さらに場合は、データの別の列の内容に基づく 1 つの列の値を検証できるように構成し、実行中に検証、<xref:System.Data.DataTable.RowChanging>イベント。
  
レコードを更新するときに、<xref:System.Data.DataTable>オブジェクトの変更が発生していると変更が加えられた後に応答してイベントを発生させます。  
  
アプリケーションでは、型指定されたデータセットを使用する場合は、厳密に型指定されたイベント ハンドラーを作成できます。 4 つの追加に型指定されたイベントのハンドラーを作成することが追加されます: `dataTableNameRowChanging`、 `dataTableNameRowChanged`、 `dataTableNameRowDeleting`、および`dataTableNameRowDeleted`です。 これらの型指定されたイベント ハンドラーは、コードを読み取りし、書き込みを容易にするテーブルの列名を含む引数を渡します。  
  
## <a name="data-update-events"></a>データ更新イベント  
  
|event|説明|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|列の値が変更されています。 イベントは、行と列を提案された新しい値とするには、渡します。|  
|<xref:System.Data.DataTable.ColumnChanged>|列の値が変更されました。 イベントは、行と列を提案された値と共に、渡します。|  
|<xref:System.Data.DataTable.RowChanging>|加えられた変更を<xref:System.Data.DataRow>オブジェクトは、データセットにコミットされます。 いないを呼び出した場合、<xref:System.Data.DataRow.BeginEdit%2A>メソッド、<xref:System.Data.DataTable.RowChanging>列への変更のイベントが発生した直後に、<xref:System.Data.DataTable.ColumnChanging>イベントが発生しました。 呼び出した場合<xref:System.Data.DataRow.BeginEdit%2A>、変更を加える前に、<xref:System.Data.DataTable.RowChanging>イベントを発生すると、呼び出した場合にのみ、<xref:System.Data.DataRow.EndEdit%2A>メソッドです。<br /><br /> イベントは、実行されるアクション (変更、挿入、およびなど) の種類を示す値とするには、行を渡します。|  
|<xref:System.Data.DataTable.RowChanged>|行が変更されました。 イベントは、実行されるアクション (変更、挿入、およびなど) の種類を示す値とするには、行を渡します。|  
|<xref:System.Data.DataTable.RowDeleting>|行を削除しています。 イベントは、実行されるアクション (削除) の種類を示す値とするには、行を渡します。|  
|<xref:System.Data.DataTable.RowDeleted>|行が削除されました。 イベントは、実行されるアクション (削除) の種類を示す値とするには、行を渡します。|  
  
<xref:System.Data.DataTable.ColumnChanging>、 <xref:System.Data.DataTable.RowChanging>、および<xref:System.Data.DataTable.RowDeleting>更新プロセス中にイベントが発生します。 これらのイベントを使用して、データの検証またはその他の種類の処理を実行することができます。 更新プログラムは、これらのイベントの中にプロセスではため、スローすることによって、例外が原因での更新プログラムを取り消すことができますを終了します。  
  
<xref:System.Data.DataTable.ColumnChanged>、<xref:System.Data.DataTable.RowChanged>と<xref:System.Data.DataTable.RowDeleted>イベントは、更新プログラムが正常に完了したときに発生するイベントを通知します。 これらのイベントは、正常な更新に基づいたのアクションを実行する場合に便利です。  
  
## <a name="validate-data-during-column-changes"></a>列の変更時にデータを検証します。  
  
> [!NOTE]
>  **データセット デザイナー**データセットに実行する検証ロジックを追加できる部分クラスを作成します。 デザイナーで生成されたデータセットは削除しないか、部分クラス内のコードを変更します。  
  
応答でのデータ列の値が変更されたときにデータを検証することができます、<xref:System.Data.DataTable.ColumnChanging>イベント。 このイベントが、イベント引数を渡して、発生したときに (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) 現在の列の提示される値を格納します。 内容に基づく`e.ProposedValue`、することができます。  
  
-   何もせずに、指示された値を受け入れます。  
  
-   列のエラーを設定して、提案された値を拒否する (<xref:System.Data.DataRow.SetColumnError%2A>) から列を変更するイベント ハンドラー内で。  
  
-   オプションで <xref:System.Windows.Forms.ErrorProvider> コントロールを使用して、ユーザーにエラー メッセージを表示します。 詳細については、次を参照してください。 [ErrorProvider コンポーネント](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)です。  
  
中に検証を実行することも、<xref:System.Data.DataTable.RowChanging>イベント。 
  
## <a name="validate-data-during-row-changes"></a>行の変更時にデータを検証します。  
検証する各列にアプリケーションの要件を満たすデータが格納されていることを検証するコードを記述できます。 これには、提案された値が許容されない場合エラーがあることを示すために、列を設定します。 `Quantity` 列が 0 以下の場合に列エラーを設定する例を次に示します。 行変更イベント ハンドラーは、次のように記述します。  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>行の変更時にデータを検証するには (Visual Basic)  
  
1.  データセットを開き、**データセット デザイナー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。  
  
2.  検証するテーブルのタイトル バーをダブルクリックします。 この操作により、データセットの部分クラス ファイルに <xref:System.Data.DataTable.RowChanging> の <xref:System.Data.DataTable> イベント ハンドラーが自動的に作成されます。  
  
    > [!TIP]
    >  テーブル名の左側をダブルクリックして、行変更イベント ハンドラーを作成します。 テーブル名をダブルクリックすると、編集することができます。  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>行の変更時にデータ検証するには (C#)  
  
1.  データセットを開き、**データセット デザイナー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。  
  
2.  検証するテーブルのタイトル バーをダブルクリックします。 この操作により、<xref:System.Data.DataTable> の部分クラス ファイルが作成されます。  
  
    > [!NOTE]
    >  **データセット デザイナー**のイベント ハンドラーを自動的に作成されません、<xref:System.Data.DataTable.RowChanging>イベント。 処理するメソッドを作成する必要がある、<xref:System.Data.DataTable.RowChanging>テーブルの初期化メソッドでイベントをフックするには、イベント、およびコードを実行します。  
  
3.  部分クラスに次のコードをコピーします。  
  
    ```csharp  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## <a name="to-retrieve-changed-rows"></a>変更された行を取得するには  
データ テーブルの行のそれぞれが、<xref:System.Data.DataRow.RowState%2A>プロパティを追跡する行の現在の状態の値を使用して、<xref:System.Data.DataRowState>列挙します。 呼び出してデータセットまたはデータ テーブルから変更された行を返すことができます、`GetChanges`のメソッド、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>です。 変更を呼び出す前に存在することを確認することができます`GetChanges`を呼び出して、<xref:System.Data.DataSet.HasChanges%2A>データセットのメソッドです。 
  
> [!NOTE]
>  データセットまたはデータ テーブルに変更をコミットした後 (呼び出すことによって、<xref:System.Data.DataSet.AcceptChanges%2A>メソッド) では、`GetChanges`メソッドにはデータは返されません。 アプリケーションは、変更された行を処理する必要がある場合、は、呼び出す前に変更を処理する必要があります、`AcceptChanges`メソッドです。  
  
呼び出す、<xref:System.Data.DataSet.GetChanges%2A>データセットまたはデータ テーブルのメソッドが変更されているレコードだけを含む新しいデータセットまたはデータ テーブルを返します。 特定のレコードを取得する場合、例については、新しいレコードにのみ、または変更されたレコードだけ — から値を渡すことができます、<xref:System.Data.DataRowState>列挙体をパラメーターとして、`GetChanges`メソッドです。  
  
使用して、<xref:System.Data.DataRowVersion>行 (たとえば、元の値が処理する前に行に含まれていた) の異なるバージョンにアクセスする列挙です。  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>変更されたすべてのレコードをデータセットから取得するには  
  
-   呼び出す、<xref:System.Data.DataSet.GetChanges%2A>データセットのメソッドです。  
  
     次の例と呼ばれる新しいデータセットを作成する`changedRecords`と呼ばれる別のデータセットから変更されたすべてのレコードの設定と`dataSet1`です。  
  
     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>データ テーブルから変更されたすべてのレコードを取得するには  
  
-   呼び出す、 <xref:System.Data.DataTable.GetChanges%2A> DataTable のメソッドです。  
  
     次の例と呼ばれる新しいデータ テーブルを作成する`changedRecordsTable`と呼ばれる別のデータ テーブルから変更されたすべてのレコードの設定と`dataTable1`です。  
  
     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>特定の行の状態にあるすべてのレコードを取得するには  
  
-   呼び出す、`GetChanges`データセットまたはデータ テーブルとパスのメソッド、<xref:System.Data.DataRowState>を引数としての列挙値。  
  
     次の例と呼ばれる新しいデータセットを作成する方法を示します`addedRecords`し、そこに追加されたレコードでのみ、`dataSet1`データセット。  
  
     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]  
  
     次の例に最近追加されたすべてのレコードを返す方法を示しています、`Customers`テーブル。  
  
     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>DataRow の元のバージョンにアクセスします。  
データ行を変更すると、データセットにその行の元のバージョン (<xref:System.Data.DataRowVersion.Original>) と新しいバージョン (<xref:System.Data.DataRowVersion.Current>) が保存されます。 たとえば、`AcceptChanges` メソッドを呼び出す前にレコードの別のバージョン (<xref:System.Data.DataRowVersion> 列挙定数で定義) にアクセスし、そのバージョンに応じて変更を処理できます。  
  
> [!NOTE]
>  異なるバージョンの行の存在が編集されました。 後でのみとする前に、`AcceptChanges`メソッドが呼び出されました。 `AcceptChanges` メソッドの呼び出し後は、現在のバージョンと元のバージョンが同じになります。  
  
<xref:System.Data.DataRowVersion> 値を列インデックス (文字列である列名) と共に渡すと、その列の特定の行バージョンから値が返されます。 中に変更された列を識別、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.ColumnChanged>イベント。 これは、検証の目的での異なる行バージョンを検査する絶好のタイミングです。 ただし、制約を一時的に中断した場合は、これらのイベントは発生しません、する必要がプログラムでは、変更された列を識別します。 <xref:System.Data.DataTable.Columns%2A> コレクションを反復処理し、異なる <xref:System.Data.DataRowVersion> 値を比較することにより変更された列を識別できます。  
  
#### <a name="to-get-the-original-version-of-a-record"></a>レコードの元のバージョンを取得するには  
  
-   渡すことで、列の値へのアクセス、<xref:System.Data.DataRowVersion>行を取得するのです。  
  
     次の例を使用する方法を示しています、<xref:System.Data.DataRowVersion>の元の値を取得する値、`CompanyName`フィールドで、 <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>DataRow の現在のバージョンにアクセスします。  
  
#### <a name="to-get-the-current-version-of-a-record"></a>レコードの現在のバージョンを取得するには  
  
-   列の値にアクセスし、インデックスを取得する行のバージョンを示すには、パラメーターを追加します。  
  
     次の例を使用する方法を示しています、<xref:System.Data.DataRowVersion>の現在の値を取得する値、`CompanyName`フィールドで、 <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]  
  
## <a name="see-also"></a>関連項目
[Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)  
[方法: Windows フォーム DataGridView コントロールでデータを検証します。](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)   
[方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)