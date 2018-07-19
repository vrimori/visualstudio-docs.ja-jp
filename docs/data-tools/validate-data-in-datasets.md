---
title: データセットのデータの検証
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a0a8846719c6ad57e65e1e308e9884e81e1997d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174723"
---
# <a name="validate-data-in-datasets"></a>データセットのデータの検証
データの検証は、データ オブジェクトに入力される値は、データセットのスキーマ内の制約に準拠することを確認するプロセスです。 また、検証プロセスは、これらの値が、アプリケーションに対して設定した規則に従っていることを確認します。 基になるデータベースの更新を送信する前にデータを検証することをお勧めします。 これには、エラーに加え、潜在的なアプリケーションとデータベース間のラウンド トリップ数が削減されます。

データセットに書き込まれたデータがデータセットに検証チェックを組み込むことで有効であるを確認できます。 データセットは、更新プログラムの実行方法に関係なく、データを確認できます: コントロール、コンポーネント内のフォームまたは他の方法で直接かどうか。 データセットが (データベースのバック エンド) とは異なり、アプリケーションの一部であるため、アプリケーション固有の検証をビルドする論理的な場所になります。

アプリケーションに検証を追加する最適な場所は、データセットの部分クラス ファイルです。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]、オープン、**データセット デザイナー**検証の対象となる列またはテーブルをダブルクリックします。 この操作は自動的に作成、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>イベント ハンドラー。

## <a name="validate-data"></a>データを検証します。
 データセット内での検証は、次の方法で実現されます。

-   変更時に個々 のデータ列の値をチェックできるアプリケーション固有の検証を作成します。 詳細については、次を参照してください。[方法: 列の変更時にデータを検証](validate-data-in-datasets.md)です。

-   データ全体の中に値にデータをチェックできるアプリケーション固有の検証を作成して、行が変更されます。 詳細については、次を参照してください。[方法: 行の変更時にデータを検証](validate-data-in-datasets.md)です。

-   これに、データセットの実際のスキーマ定義の一部としてキー、一意の制約を作成します。

-   プロパティを設定して、<xref:System.Data.DataColumn>オブジェクトのなど<xref:System.Data.DataColumn.MaxLength%2A>、 <xref:System.Data.DataColumn.AllowDBNull%2A>、および<xref:System.Data.DataColumn.Unique%2A>します。

によって複数のイベントが発生する、<xref:System.Data.DataTable>オブジェクトのレコードの変更が発生している場合。

-   <xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.ColumnChanged>中およびそれぞれ個々 の列の変更後のイベントが発生します。 <xref:System.Data.DataTable.ColumnChanging>イベントは、特定の列で変更を検証する場合に便利です。 提案された変更については、イベントの引数として渡されます。
-   <xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>イベントが発生中と後に行の変更。 <xref:System.Data.DataTable.RowChanging>イベントは一般的な。 これは、変更が、行のどこかに発生しているが、どの列が変更されたがわからないことを示します。

既定では、それぞれの列の変更はそのため 4 つのイベントを生成します。 1 つは、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.ColumnChanged>が変更されている特定の列のイベント。 次に、<xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>イベント。 行に複数の変更が行わ、イベントが各変更に対して発生します。

> [!NOTE]
>  データ行の<xref:System.Data.DataRow.BeginEdit%2A>メソッドがオフ、<xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>それぞれ個々 の列の変更後のイベント。 までイベントが発生しない場合、<xref:System.Data.DataRow.EndEdit%2A>メソッドが呼び出されて、ときに、<xref:System.Data.DataTable.RowChanging>と<xref:System.Data.DataTable.RowChanged>イベントは 1 回だけ発生します。 詳細については、次を参照してください。[データセットの読み込み中に制約を無効に](../data-tools/turn-off-constraints-while-filling-a-dataset.md)します。

選択したイベントを検証したい粒度によって異なります。 列が変更されたときすぐには、エラーをキャッチすることが重要である場合を使用して検証をビルド、<xref:System.Data.DataTable.ColumnChanging>イベント。 それ以外の場合、使用、<xref:System.Data.DataTable.RowChanging>イベントで、一度にいくつかのエラーをキャッチする可能性があります。 さらに、別の列の内容に基づく 1 つの列の値を検証できるように、データは構造化されている場合は、実行中に検証、<xref:System.Data.DataTable.RowChanging>イベント。

レコードを更新するときに、<xref:System.Data.DataTable>オブジェクトの変更が発生していると変更された後に応答するイベントを発生させます。

アプリケーションでは、型指定されたデータセットを使用する場合は、厳密に型指定されたイベント ハンドラーを作成できます。 次の 4 つ追加の型指定されたイベント ハンドラーを作成できますが追加されます: `dataTableNameRowChanging`、 `dataTableNameRowChanged`、 `dataTableNameRowDeleting`、および`dataTableNameRowDeleted`します。 これらの型指定されたイベント ハンドラーは、書き込みと読み取りのコードを簡単にするテーブルの列名を含む引数を渡します。

## <a name="data-update-events"></a>データ更新イベント

|event|説明|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|列の値が変更されています。 イベントは、行と列を提示された新しい値と共にに渡します。|
|<xref:System.Data.DataTable.ColumnChanged>|列の値が変更されました。 イベントは、行と列を指定された値と共に、渡します。|
|<xref:System.Data.DataTable.RowChanging>|加えられた変更を<xref:System.Data.DataRow>オブジェクトは、データセットにコミットされます。 呼び出さない場合、<xref:System.Data.DataRow.BeginEdit%2A>メソッド、<xref:System.Data.DataTable.RowChanging>列には、各変更のイベントが発生した後すぐに、<xref:System.Data.DataTable.ColumnChanging>イベントが発生しました。 呼び出した場合<xref:System.Data.DataRow.BeginEdit%2A>、変更を加える前に、<xref:System.Data.DataTable.RowChanging>を呼び出すときにのみイベントが発生、<xref:System.Data.DataRow.EndEdit%2A>メソッド。<br /><br /> イベントは、実行されるアクション (変更、挿入、およびなど) の種類を示す値と共に、行を渡します。|
|<xref:System.Data.DataTable.RowChanged>|行が変更されました。 イベントは、実行されるアクション (変更、挿入、およびなど) の種類を示す値と共に、行を渡します。|
|<xref:System.Data.DataTable.RowDeleting>|行を削除しています。 イベントは、実行されるアクション (削除) の種類を示す値と共に、行を渡します。|
|<xref:System.Data.DataTable.RowDeleted>|行が削除されました。 イベントは、実行されるアクション (削除) の種類を示す値と共に、行を渡します。|

<xref:System.Data.DataTable.ColumnChanging>、 <xref:System.Data.DataTable.RowChanging>、および<xref:System.Data.DataTable.RowDeleting>更新プロセス中にイベントが発生します。 これらのイベントを使用して、データの検証またはその他の種類の処理を実行することができます。 更新がこれらのイベント中にプロセスのため、更新プログラムを実行できなくなりますが、例外をスローしてキャンセルできますを終了します。

<xref:System.Data.DataTable.ColumnChanged>、<xref:System.Data.DataTable.RowChanged>と<xref:System.Data.DataTable.RowDeleted>イベントは、更新が正常に完了したときに発生するイベントを通知します。 これらのイベントは、正常な更新に基づいたアクションを実行する場合に便利です。

## <a name="validate-data-during-column-changes"></a>列の変更時にデータを検証します。

> [!NOTE]
>  **データセット デザイナー**データセットに実行する検証のロジックを追加できます部分クラスを作成します。 デザイナーで生成されたデータセットは、削除または部分クラス内のコードを変更しません。

データを検証するには、データ列の値が応答することで変更されたときに、<xref:System.Data.DataTable.ColumnChanging>イベント。 発生すると、このイベントはイベント引数を渡します (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) は、現在の列の提示された値を格納します。 内容に基づく`e.ProposedValue`を実行できます。

-   何もせずに、指示された値を受け入れます。

-   列のエラーを設定して指定された値を拒否する (<xref:System.Data.DataRow.SetColumnError%2A>) から列を変更するイベント ハンドラー内にします。

-   オプションで <xref:System.Windows.Forms.ErrorProvider> コントロールを使用して、ユーザーにエラー メッセージを表示します。 詳細については、次を参照してください。 [ErrorProvider コンポーネント](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)します。

中に検証を実行することも、<xref:System.Data.DataTable.RowChanging>イベント。

## <a name="validate-data-during-row-changes"></a>行の変更時にデータを検証します。
検証する各列にアプリケーションの要件を満たすデータが格納されていることを検証するコードを記述できます。 そうで提案された値が許容されない場合、エラーが含まれているかを示す列を設定します。 `Quantity` 列が 0 以下の場合に列エラーを設定する例を次に示します。 行変更イベント ハンドラーは、次のように記述します。

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>行の変更時にデータを検証するには (Visual Basic)

1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)します。

2.  検証するテーブルのタイトル バーをダブルクリックします。 この操作により、データセットの部分クラス ファイルに <xref:System.Data.DataTable.RowChanging> の <xref:System.Data.DataTable> イベント ハンドラーが自動的に作成されます。

    > [!TIP]
    >  テーブル名の左側をダブルクリックして、行変更イベント ハンドラーを作成します。 テーブル名をダブルクリックすると、編集することができます。

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>行の変更時にデータ検証するには (C#)

1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)します。

2.  検証するテーブルのタイトル バーをダブルクリックします。 この操作により、<xref:System.Data.DataTable> の部分クラス ファイルが作成されます。

    > [!NOTE]
    >  **データセット デザイナー**のイベント ハンドラーを自動的に作成されません、<xref:System.Data.DataTable.RowChanging>イベント。 処理するメソッドを作成する必要がある、<xref:System.Data.DataTable.RowChanging>テーブルの初期化メソッドでイベントにフックするには、イベント、およびコードを実行します。

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
データ テーブルの各行が、<xref:System.Data.DataRow.RowState%2A>で値を使用してその行の現在の状態はの追跡プロパティ、<xref:System.Data.DataRowState>列挙体。 呼び出すことによって、データセットまたはデータ テーブルから変更された行を返すことができます、`GetChanges`のメソッド、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>します。 変更を呼び出す前に存在することを確認できる`GetChanges`呼び出すことによって、<xref:System.Data.DataSet.HasChanges%2A>データセットのメソッド。

> [!NOTE]
>  データセットまたはデータ テーブルに変更をコミットした後 (呼び出すことによって、<xref:System.Data.DataSet.AcceptChanges%2A>メソッド)、`GetChanges`メソッドにはデータは返されません。 を、アプリケーションが変更された行を処理する必要がある場合は、呼び出す前に変更を処理する必要があります、`AcceptChanges`メソッド。

呼び出す、<xref:System.Data.DataSet.GetChanges%2A>データセットまたはデータ テーブルのメソッドが変更されているレコードだけを含む新しいデータセットまたはデータ テーブルを返します。 特定のレコードを取得する場合: の例では、新しいレコードにのみ、または変更されたレコードのみ-から値を渡すことができます、<xref:System.Data.DataRowState>列挙体をパラメーターとして、`GetChanges`メソッド。

使用して、<xref:System.Data.DataRowVersion>行 (たとえば、元の値が処理する前に行に含まれていた) のさまざまなバージョンにアクセスする列挙体。

### <a name="to-get-all-changed-records-from-a-dataset"></a>データセットから変更されたすべてのレコードを取得するには

-   呼び出す、<xref:System.Data.DataSet.GetChanges%2A>データセットのメソッド。

     次の例と呼ばれる新しいデータセットを作成する`changedRecords`しという別のデータセットから変更されたすべてのレコードを追加します`dataSet1`します。

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>データ テーブルから変更されたすべてのレコードを取得するには

-   呼び出す、 <xref:System.Data.DataTable.GetChanges%2A> DataTable のメソッド。

     次の例と呼ばれる新しいデータ テーブルを作成する`changedRecordsTable`しと呼ばれる別のデータ テーブルから変更されたすべてのレコードを追加します`dataTable1`します。

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>特定の行の状態を持つすべてのレコードを取得するには

-   呼び出す、`GetChanges`データセットまたはデータ テーブルとパスのメソッドを<xref:System.Data.DataRowState>を引数としての列挙値。

     次の例は、という名前の新しいデータセットを作成する方法を示しています。`addedRecords`し、そこに追加されたレコードでのみ、`dataSet1`データセット。

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     次の例に最近追加されたすべてのレコードを返す方法を示しています、`Customers`テーブル。

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>DataRow の元のバージョンへのアクセスします。
データ行を変更すると、データセットにその行の元のバージョン (<xref:System.Data.DataRowVersion.Original>) と新しいバージョン (<xref:System.Data.DataRowVersion.Current>) が保存されます。 たとえば、`AcceptChanges` メソッドを呼び出す前にレコードの別のバージョン (<xref:System.Data.DataRowVersion> 列挙定数で定義) にアクセスし、そのバージョンに応じて変更を処理できます。

> [!NOTE]
>  異なるバージョンの行の存在が編集後にのみ、その前に、`AcceptChanges`メソッドが呼び出されました。 `AcceptChanges` メソッドの呼び出し後は、現在のバージョンと元のバージョンが同じになります。

<xref:System.Data.DataRowVersion> 値を列インデックス (文字列である列名) と共に渡すと、その列の特定の行バージョンから値が返されます。 中に変更された列が識別される、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.ColumnChanged>イベント。 これは、検証のための異なる行バージョンを検査するよい機会です。 ただし、制約を一時的に中断されますが、これらのイベントは発生しません、およびプログラムを使用する必要がある場合は、変更された列を識別します。 <xref:System.Data.DataTable.Columns%2A> コレクションを反復処理し、異なる <xref:System.Data.DataRowVersion> 値を比較することにより変更された列を識別できます。

### <a name="to-get-the-original-version-of-a-record"></a>レコードの元のバージョンを取得するには

-   渡すことで、列の値へのアクセス、<xref:System.Data.DataRowVersion>を取得する行のできます。

     次の例は、使用する方法を示します、<xref:System.Data.DataRowVersion>の元の値を取得する値を`CompanyName`フィールドに、 <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>DataRow の現在のバージョンへのアクセスします。

### <a name="to-get-the-current-version-of-a-record"></a>レコードの現在のバージョンを取得するには

-   列の値にアクセスし、し、パラメーターを取得する行のバージョンを示すインデックスを追加します。

     次の例は、使用する方法を示します、<xref:System.Data.DataRowVersion>の現在の値を取得する値を`CompanyName`フィールドに、 <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>関連項目

- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)
- [方法: Windows フォーム DataGridView コントロールでデータを検証します。](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証のエラー アイコンを表示](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)