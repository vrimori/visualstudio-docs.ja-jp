---
title: データをデータベースに保存 |Microsoft Docs
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
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b6fd99b2b1a41d6baa3a110b2a595afb1dd7e3f
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281850"
---
# <a name="save-data-back-to-the-database"></a>データをデータベースに保存する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
データセットは、データのインメモリ コピーです。 そのデータを変更する場合は、これらの変更をデータベースに保存することをお勧めします。 これには 3 つの方法のいずれかの操作を行います。  
  
- いずれかを呼び出すことによって、 `Update` TableAdapter のメソッド  
  
- TableAdapter の DBDirect メソッドのいずれかを呼び出す  
  
- UpdateAll メソッドを呼び出すことによって、 `TableAdapterManager` Visual Studio は、データセットには、データセット内の他のテーブルに関連するテーブルが含まれている場合を生成します。  
  
  Windows フォームまたは XAML ページ上のコントロールをデータセットのテーブルをバインドするデータとデータ バインディング アーキテクチャは、すべての作業をするは。  
  
  Tableadapter を使い慣れているの場合は、これらのトピックのいずれかに直接ジャンプできます。  
  
|トピック|説明|  
|-----------|-----------------|  
|[データベースに新しいレコードを挿入する](../data-tools/insert-new-records-into-a-database.md)|実行する方法を更新し、Tableadapter またはコマンド オブジェクトを使用して挿入|  
|[TableAdapter を使用してデータを更新する](../data-tools/update-data-by-using-a-tableadapter.md)|Tableadapter が更新を実行する方法|  
|[階層更新](../data-tools/hierarchical-update.md)|2 つ以上の関連テーブルを含むデータセットから更新プログラムを実行する方法|  
|[コンカレンシー例外を処理する](../data-tools/handle-a-concurrency-exception.md)|2 人のユーザーが、同時に、データベース内の同じデータを変更しようとしています。 ときに例外を処理する方法|  
|[トランザクションを使用してデータを保存する](../data-tools/save-data-by-using-a-transaction.md)|System.Transactions 名前空間と、TransactionScope オブジェクトを使用してトランザクションでデータを保存する方法|  
|[トランザクションにデータを保存する](../data-tools/save-data-in-a-transaction.md)|System.Transactions 名前空間を使用して、トランザクションでデータを保存する方法|  
|[データベースへのデータの保存 (複数テーブル)](../data-tools/save-data-to-a-database-multiple-tables.md)|レコードを編集し、元のデータベースに複数のテーブルで変更を保存する方法|  
|[オブジェクトからデータベースにデータを保存する](../data-tools/save-data-from-an-object-to-a-database.md)|TableAdapter DbDirect メソッドを使用してデータベースへのデータセットではないオブジェクトからデータを渡す方法|  
|[TableAdapter DBDirect メソッドを使用してデータを保存する](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|TableAdapter を使用して、データベースに直接 SQL クエリを送信する方法|  
|[データセットを XML として保存する](../data-tools/save-a-dataset-as-xml.md)|XML ドキュメントにデータセットを保存する方法|  
  
## <a name="two-stage-updates"></a>2 段階の更新  
 2 段階のプロセスは、データ ソースを更新します。 最初の手順では、新しいレコード、変更されたレコード、または削除されたレコードでデータセットを更新します。 アプリケーションは、データ ソースに戻ることはありませんこれらの変更を送信する場合を完了すると、更新されます。  
  
 元のデータベースに変更を送信する場合、次の手順が必要です。 データ バインド コントロールを使用していない場合は手動でデータセットを作成するために使用する同じ TableAdapter (またはデータ アダプター) の Update メソッドを呼び出す必要があります。 ただし、1 つのデータ ソースからデータを移動する、または複数のデータ ソースを更新するも別のアダプターを使用することができます。 データ バインディングを使用していないし、関連テーブルの変更を保存していますがある場合、自動生成された TableAdapterManager クラスの変数を手動でインスタンス化し、その UpdateAll メソッドを呼び出します。  
  
 ![Visual Basic データセット更新](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
2 段階の更新プロセスと、正常な更新における DataRowVersion の役割  
  
 データセットには、行のコレクションを含むテーブルのコレクションが含まれています。 後で、基になるデータ ソースを更新する場合は、DataTable.DataRowCollection プロパティを追加または行を削除するときにメソッドを使用する必要があります。 これらのメソッドは、データ ソースを更新するために必要な変更の追跡を実行します。 RemoveAt コレクション行のプロパティを呼び出す場合、削除を元のデータベースに伝達されません。  
  
## <a name="merge-datasets"></a>データセットをマージします。  
 データセットの内容を更新する*マージ*で別のデータセット。 内容をコピーするためにこれを*ソース*に呼び出し元のデータセットのデータセット (と呼ばれる、*ターゲット*データセット)。 データセットをマージすると、ソース データセットの新しいレコードはターゲット データセットに追加されます。 また、ソース データセットのその他の列もターゲット データセットに追加されます。 ローカル データセットを用意して、別のアプリケーションから 2 番目のデータセットを取得する場合は、データセットをマージすると便利です。 XML web サービスなどのコンポーネントから 2 番目のデータセットが表示された場合、または複数のデータセットからデータを統合する必要がある場合にも便利です。  
  
 データセットをマージするときに、ブール型の引数を渡すことができます (`preserveChanges`) を示す、<xref:System.Data.DataSet.Merge%2A>メソッド ターゲット データセットの既存の変更を保持するかどうか。 データセットのレコードの複数のバージョン管理、ためには、レコードの 1 つ以上のバージョンがマージされることを念頭に重要です。 次の表は、2 つのデータセット内のレコードをマージする方法を示しています。  
  
|DataRowVersion|ターゲット データセット|ソース データセット|  
|--------------------|--------------------|--------------------|  
|元|James Wilson|James C. Wilson|  
|現在|Jim Wilson|James C. Wilson|  
  
 呼び出す、<xref:System.Data.DataSet.Merge%2A>メソッドで、前の表を`preserveChanges=false targetDataset.Merge(sourceDataset)`結果、次の。  
  
|DataRowVersion|ターゲット データセット|ソース データセット|  
|--------------------|--------------------|--------------------|  
|元|James C. Wilson|James C. Wilson|  
|現在|James C. Wilson|James C. Wilson|  
  
 <xref:System.Data.DataSet.Merge%2A> である場合に `preserveChanges = true targetDataset.Merge(sourceDataset, true)` メソッドを呼び出すと、結果は次のようになります。  
  
|DataRowVersion|ターゲット データセット|ソース データセット|  
|--------------------|--------------------|--------------------|  
|元|James C. Wilson|James C. Wilson|  
|現在|Jim Wilson|James C. Wilson|  
  
> [!CAUTION]
>  `preserveChanges = true`シナリオでは場合、<xref:System.Data.DataSet.RejectChanges%2A>メソッドは、ターゲット データセットのレコードにし、元のデータに戻ります、*ソース*データセット。 これは、ことをターゲット データセットによって元のデータ ソースを更新しようとすると、その可能性がありますできないことを意味を更新する元の行を検索します。 データ ソースからレコードの更新された別のデータセットを入力し、同時実行制御違反を防ぐために、マージを実行することによって、同時実行制御違反を防ぐことができます。 (コンカレンシー違反は、データセットにレコードが格納された後で別のユーザーがデータ ソース内のレコードを変更すると発生します。)  
  
## <a name="update-constraints"></a>制約を更新します。  
 既存のデータ行を変更するには、追加または個々 の列のデータを更新します。 データセットに制約 (外部キー、null 非許容の制約など) が含まれている場合は、更新するとき、レコードはエラー状態にする一時的にあります。 1 つの列の更新の終了後、次のいずれかを取得する前に、エラー状態にする、ことができます。  
  
 早期に制約違反を防ぐために、更新制約を一時的に中断できます。 これには 2 つの目的があります。  
  
- 1 つの列の更新が完了したら、別の更新を開始していないが後にスローされないエラーができないようにします。  
  
- 特定の更新は阻止されてからのイベントには (多くの場合、検証に使用されるイベント) が発生します。  
  
  更新プログラムを完了すると、有効にできます再制約チェックをする更新プログラムのイベントを再度有効にしが発生します。  
  
> [!NOTE]
>  Windows フォームでのデータ グリッドに組み込まれているデータ バインディング アーキテクチャは、フォーカスが、行外に移動しを明示的に呼び出していないまで制約チェックを中断、 <xref:System.Data.DataRow.BeginEdit%2A>、 <xref:System.Data.DataRow.EndEdit%2A>、または<xref:System.Data.DataRow.CancelEdit%2A>メソッド。  
  
 データセットで <xref:System.Data.DataSet.Merge%2A> メソッドが呼び出されると、制約は自動的に無効になります。 マージが完了したら、有効にするデータセットに対するすべての制約がある場合、<xref:System.Data.ConstraintException>がスローされます。 この場合、<xref:System.Data.DataSet.EnforceConstraints%2A> プロパティが `false,` に設定されるので、すべての制約違反を解決してから <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティを `true` に設定し直す必要があります。  
  
 更新プログラムを完了すると、有効にできます再制約チェックをする更新プログラムのイベントを再度有効にしが発生します。  
  
 イベントの中断に関する詳細については、次を参照してください。[データセットの読み込み中に制約を無効に](../data-tools/turn-off-constraints-while-filling-a-dataset.md)します。  
  
## <a name="dataset-update-errors"></a>データセット更新エラー  
 データセットのレコードを更新するときにエラーが発生する場合があります。 たとえばを列に無効な型のデータまたはデータが長すぎる、またはその他の整合性の問題のあるデータを誤って書き込んだ場合があります。 または、更新イベントのいずれかの段階中にカスタム エラーを引き起こすアプリケーション固有の検証チェックする必要があります。 詳細については、次を参照してください。[検証データセットのデータの](../data-tools/validate-data-in-datasets.md)します。  
  
## <a name="maintaining-information-about-changes"></a>変更に関する情報を保持  
 2 つの方法でデータセットの変更に関する情報を保持: 行が変更されていることを示すフラグを設定 (<xref:System.Data.DataRow.RowState%2A>)、およびレコードの複数のコピーを保持することで (<xref:System.Data.DataRowVersion>)。 変更に関する情報を使用することにより、プロセスはデータセットの変更内容を確認し、適切な更新内容をデータ ソースに送信できます。  
  
### <a name="rowstate-property"></a>RowState プロパティ  
 <xref:System.Data.DataRow.RowState%2A> オブジェクトの <xref:System.Data.DataRow> プロパティは、データの特定の行のステータスに関する情報を提供する値です。  
  
 <xref:System.Data.DataRowState> 列挙定数に使用できる値の詳細を次の表に示します。  
  
|DataRowState 列挙定数の値|説明|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState>|行は項目として <xref:System.Data.DataRowCollection> に追加されました。 (この状態の行は存在しなかったため、対応する元のバージョンがないときに、最終<xref:System.Data.DataRow.AcceptChanges%2A>メソッドが呼び出されました)。|  
|<xref:System.Data.DataRowState>|行は <xref:System.Data.DataRow.Delete%2A> オブジェクトの <xref:System.Data.DataRow> を使用して削除されました。|  
|<xref:System.Data.DataRowState>|行は作成されましたが、<xref:System.Data.DataRowCollection> の一部ではありません。 A<xref:System.Data.DataRow>がコレクションから削除された後、それが作成されたら、前が追加されました、コレクションにすぐに、オブジェクトがこの状態にします。|  
|<xref:System.Data.DataRowState>|行の列の値は、何らかの方法で変更されました。|  
|<xref:System.Data.DataRowState>|行は <xref:System.Data.DataRow.AcceptChanges%2A> が最後に呼び出されてから変更されていません。|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion 列挙型  
 データセットはレコードの複数のバージョンを保持します。 <xref:System.Data.DataRowVersion> オブジェクトの <xref:System.Data.DataRow> 列挙定数を使用すると、特定のバージョンの <xref:System.Data.DataRow> オブジェクトを取得できます。  
  
 <xref:System.Data.DataRowVersion> 列挙定数に使用できる値の詳細を次の表に示します。  
  
|DataRowVersion 列挙定数の値|説明|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|レコードの現在のバージョンには、レコードで前回実行されたすべての変更が含まれています。<xref:System.Data.DataRow.AcceptChanges%2A>が呼び出されました。 行が削除されている場合、現在のバージョンはありません。|  
|<xref:System.Data.DataRowVersion>|データセット スキーマまたはデータ ソースにより定義されたレコードの既定値です。|  
|<xref:System.Data.DataRowVersion>|レコードの元のバージョンは、データセットで最後の変更がコミットされたときのレコードのコピーです。 つまり、通常はデータ ソースから読み込まれたときのレコードのバージョンです。|  
|<xref:System.Data.DataRowVersion>|更新中は一時的に使用できるレコードの提案されたバージョン: というまでの時間は、<xref:System.Data.DataRow.BeginEdit%2A>メソッドと<xref:System.Data.DataRow.EndEdit%2A>メソッド。 通常は <xref:System.Data.DataTable.RowChanging> などのイベントのハンドラーで、レコードの提案されたバージョンにアクセスします。 <xref:System.Data.DataRow.CancelEdit%2A> メソッドを呼び出すと、変更は無効になり、データ行の提案されたバージョンは削除されます。|  
  
 元のバージョンおよび現在のバージョンは、更新情報をデータ ソースに送信する場合に役立ちます。 通常、更新情報をデータ ソースに送信すると、データベースの新しい情報がレコードの現在のバージョンに含まれます。 元のバージョンの情報は、更新するレコードを見つけるために使用されます。  
  
 たとえば、レコードの主キーが変更されている場合は、変更内容を更新するには、データ ソース内で適切なレコードを検索する方法が必要です。 元のバージョンがなかった場合、レコードはデータ ソースに追加される可能性が高く、結果として不要なレコードが作成されるだけでなく、不正確な古いレコードが 1 つ作成されることになります。 2 つのバージョンは、同時実行制御にも使用されます。 データセットに読み込まれた後に、レコードが変更されたかどうか、データ ソースのレコードの元のバージョンを比較することができます。  
  
 提案されたバージョンは、実際に変更をデータセットにコミットする前に検証が必要な場合に役立ちます。  
  
 レコードが変更されていても、その行の元のバージョンまたは現在のバージョンが必ず存在するわけではありません。 新しい行をテーブルに挿入した場合、元のバージョンは存在せず、現在のバージョンがあるだけです。 同様に、テーブルの `Delete` メソッドを呼び出すことにより行を削除した場合、元のバージョンはありますが現在のバージョンはありません。  
  
 データ行の <xref:System.Data.DataRow.HasVersion%2A> メソッドを照会することにより、レコードの特定のバージョンが存在するかどうかを確認するテストを行うことができます。 列の値を要求するときに <xref:System.Data.DataRowVersion> 列挙値をオプションの引数として渡すことにより、レコードのいずれかのバージョンにアクセスできます。  
  
## <a name="getting-changed-records"></a>変更されたレコードを取得します。  
 データセット内のすべてのレコードを更新するには、されません一般的なことをお勧めします。 たとえば、多数のレコードを表示する Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールをユーザーが使用しているとします。 このとき、ユーザーが一部のレコードだけを更新し、レコードを 1 つ削除し、新しいレコードを 1 つ挿入したとします。 そのような場合のために、データセットおよびデータ テーブルには、変更された行だけを返すためのメソッド (`GetChanges`) が用意されています。  
  
 データ テーブルの `GetChanges` メソッド (<xref:System.Data.DataTable.GetChanges%2A>) またはデータセットの <xref:System.Data.DataSet.GetChanges%2A> メソッド () を使って、変更されたレコードのサブセットを作成できます。 データ テーブルのメソッドを呼び出すと、変更されたレコードだけを含むテーブルのコピーが返されます。 同様に、データセットのメソッドを呼び出すと、変更されたレコードだけを含む新しいデータセットを取得できます。  
  
 `GetChanges` 自体によって変更されたすべてのレコードを返します。 目的を渡すことによってこれに対し、<xref:System.Data.DataRowState>へのパラメーターとして、`GetChanges`メソッドでは、変更されたレコードのサブセットを指定できます: 新たにデタッチされたレコードのレコード、削除対象としてマークされているレコードを追加または変更されたレコード。  
  
 レコードを処理するための別のコンポーネントに送信する場合は、変更されたレコードのサブセットを取得すると便利です。 データセット全体を送信する代わりに、コンポーネントが必要としているレコードだけを取得することにより、ほかのコンポーネントとの通信によるオーバーヘッドを小さくできます。 詳細については、次を参照してください。[方法: 変更された行の取得](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)します。  
  
## <a name="committing-changes-in-the-dataset"></a>データセットの変更をコミットします。  
 データセットを変更すると、変更された行の <xref:System.Data.DataRow.RowState%2A> プロパティが設定されます。 レコードの元と現在のバージョンの確立、維持、および入手できるようにして、<xref:System.Data.DataRowView.RowVersion%2A>プロパティ。 これらの変更された行のプロパティに格納されているメタデータは、データ ソースに適切な更新プログラムを送信する必要があります。  
  
 変更内容がデータ ソースの現在の状態を反映している場合は、この情報を保持する必要はなくなります。 通常が 2 つありますが、データセットとそのソースの同期。  
  
- ソースからデータを読み込んだときなど、情報をデータセットに読み込んだ直後。  
  
- データセットからデータ ソースに変更を送信した後 (が前ではなく、に変更をデータベースに送信するために必要な情報の変更が失われるため)。  
  
  保留中の変更は、<xref:System.Data.DataSet.AcceptChanges%2A> メソッドを呼び出してデータセットにコミットできます。 通常、<xref:System.Data.DataSet.AcceptChanges%2A>アプリケーションでは、次の時間中に呼び出されます。  
  
- した後、データセットを読み込みます。 TableAdapter の `Fill` メソッドを呼び出すことによりデータセットを読み込んだ場合、TableAdapter により変更が自動的にコミットされます。 ただし、別のデータセットをマージすることによりデータセットを読み込む場合は、変更を手動でコミットする必要があります。  
  
  > [!NOTE]
  >  アダプターが自動的に呼び出すときに、変更のコミット防止、`Fill`設定することによって、`AcceptChangesDuringFill`するアダプターのプロパティ`false`します。 設定されている場合`false`、<xref:System.Data.DataRow.RowState%2A>に設定されますが、読み込み中に挿入される行はごとの<xref:System.Data.DataRowState>します。  
  
- 後に、データセットの変更を XML Web サービスなどの別のプロセスに送信します。  
  
  > [!CAUTION]
  >  この方法で変更をコミットすると、変更情報はすべて削除されます。 いない変更をコミットするまでした後は、データセットに加えられた変更内容を把握するアプリケーションを必要とする操作を実行する完了します。  
  
  この方法で実行できる処理は次のとおりです。  
  
- 書き込みます、<xref:System.Data.DataRowVersion>にレコードのバージョンの<xref:System.Data.DataRowVersion>バージョンと元のバージョンを上書きします。  
  
- 任意の行を削除します。 場所、<xref:System.Data.DataRow.RowState%2A>プロパティに設定されて<xref:System.Data.DataRowState>します。  
  
- レコードの <xref:System.Data.DataRow.RowState%2A> プロパティを <xref:System.Data.DataRowState> に設定する。  
  
  <xref:System.Data.DataSet.AcceptChanges%2A> メソッドは、3 つのレベルで利用可能です。 呼び出すことができます、<xref:System.Data.DataRow>行にだけコミットするオブジェクトを変更します。 も呼び出すことができます、<xref:System.Data.DataTable>テーブル内のすべての行をコミットするオブジェクト。 呼び出し、最後に、<xref:System.Data.DataSet>データセットのすべてのテーブルのすべてのレコード内のすべての保留中の変更をコミットするオブジェクト。  
  
  メソッドが呼び出されたオブジェクトに基づいてコミットされる変更を次の表に示します。  
  
|メソッド|結果|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|変更は、特定の行にのみコミットされます。|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|変更は、特定のテーブルのすべての行にコミットされます。|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|変更は、データセットのすべてのテーブルのすべての行にコミットされます。|  
  
> [!NOTE]
>  TableAdapter を呼び出すことによってデータセットを読み込むかどうか`Fill`メソッドを明示的に変更を反映する必要はありません。 既定で、`Fill`メソッドの呼び出し、`AcceptChanges`データ テーブルの作成が完了した後のメソッド。  
  
 関連するメソッド、 `RejectChanges`、コピーすることで変更の効果を元に戻します、<xref:System.Data.DataRowVersion>バージョンに戻す、<xref:System.Data.DataRowVersion>レコードのバージョン。 また、設定、<xref:System.Data.DataRow.RowState%2A>各レコードの<xref:System.Data.DataRowState>します。  
  
## <a name="data-validation"></a>データの検証  
 アプリケーションのデータが、渡される対象プロセスの要件を満たしているかどうかを検査するために、検証を追加することが必要な場合もあります。 フォーム内のユーザーのエントリが正しいこと、他のアプリケーションで、アプリケーションに送信されるデータの検証またはコンポーネント内で計算される情報が、データ ソースの制約内にあるもチェックであるこのが含まれますアプリケーションの要件です。  
  
 データを検証するには次の方法があります。  
  
- ビジネス層で、データを検証するコードをアプリケーションに追加する。 データセットでこれを行うことができます。 データセットでは、列および行の値が変更されるたびに変更を検証する機能など、バック エンド検証を活用できます。 詳細については、次を参照してください。[検証データセットのデータの](../data-tools/validate-data-in-datasets.md)します。  
  
- プレゼンテーション層で、検証をフォームに追加する。 詳細については、次を参照してください。 [Windows フォームでのユーザーの入力検証](http://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1)です。  
  
- データのバック エンドで、データをデータベースなどのデータ ソースに送信し、データの受け入れまたは拒否を行うことができるようにする。 データの検証やエラー情報を提供する洗練された機能を備えたデータベースを使用している場合、実用的なアプローチになります。データのソースが何であるかにかかわらずデータを検証できるからです。 ただし、このアプローチはアプリケーション固有の検証要件に対応しない可能性があります。 さらに、アプリケーションが、バック エンドによって発生した検証エラーの解決を容易にする方法に応じて、データ ソースにラウンド トリップが多数データ ソースでデータの検証が結果ことができます。  
  
  > [!IMPORTANT]
  >  データ コマンドを使用する場合、<xref:System.Data.SqlClient.SqlCommand.CommandType%2A>プロパティに設定されている<xref:System.Data.CommandType>、慎重に、データベースに渡す前に、クライアントから送信される情報を確認します。 悪意のあるユーザーが、承認なしでデータベースにアクセスしたり、データベースを破壊したりする目的で、変更した SQL ステートメントや追加の SQL ステートメントの送信 (挿入) を試みる場合があります。 ユーザーの入力をデータベースを転送する前に常に情報が有効なことを確認します。 常にパラメーター化クエリまたは可能であればストアド プロシージャを使用することをお勧めします。 詳細については、「[スクリプトによる攻略の概要](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)」を参照してください。  
  
  データセットを変更した後で、変更内容をデータ ソースに転送できます。 一般に、これは TableAdapter (またはデータ アダプター) の `Update` メソッドを呼び出すことによって行います。 データ テーブル内の各レコードのループのメソッドでは、必要な更新プログラムの種類を決定します (更新、挿入、または削除) があれば、適切なコマンドを実行します。  
  
## <a name="transmitting-updates-to-the-data-source"></a>データ ソースに送信して更新プログラム  
 更新を行う方法の図解は、アプリケーションを 1 つのデータ テーブルを含むデータセットを使用するとします。 アプリケーションはデータベースから 2 つの行をフェッチします。 行の取得後、インメモリ データ テーブルは次のようになります。  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 アプリケーションによって Nancy Buchanan のステータスが "Preferred" に変更されます。 この変更の結果、その行の <xref:System.Data.DataRow.RowState%2A> プロパティの値は、<xref:System.Data.DataRowState> から <xref:System.Data.DataRowState> に変更されます。 最初の行の <xref:System.Data.DataRow.RowState%2A> プロパティの値は、<xref:System.Data.DataRowState> のままです。 データ テーブルは次のようになります。  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 アプリケーションは `Update` メソッドを呼び出し、データセットをデータベースに転送します。 このメソッドは各行を順に調べます。 最初の行に転送されません SQL ステートメントはデータベースにデータベースからフェッチされたために、その行が変更されていないためです。  
  
 ただし、2 番目の行について、`Update`メソッドが自動的に正しいデータ コマンドを呼び出すし、データベースに転送します。 特定の SQL ステートメントの構文は、基になるデータ ストアでサポートされている SQL の言語に依存します。 ただし、転送される SQL ステートメントには次のような一般的な特徴があります。  
  
-   転送される SQL ステートメントは UPDATE ステートメントである。 <xref:System.Data.DataRow.RowState%2A> プロパティの値が <xref:System.Data.DataRowState> であるため、このアダプターは UPDATE ステートメントを使用します。  
  
-   転送される SQL ステートメントには、UPDATE ステートメントのターゲットが、行であることを示す WHERE 句が含まれています、`CustomerID = 'c400'`します。 `CustomerID` は転送先のテーブルの主キーであるため、SELECT ステートメントのこの部分により転送先の行を他の行と区別します。 WHERE 句の派生のレコードの元のバージョンに関する情報 (`DataRowVersion.Original`) 行を識別するために必要な値が変更されました場合。  
  
-   転送される SQL ステートメントには SET 句が含まれており、変更された列の新しい値を設定する。  
  
    > [!NOTE]
    >  TableAdapter の `UpdateCommand` プロパティにストアド プロシージャの名前が設定されている場合、TableAdapter は SQL ステートメントを作成しません。 その代わりに、適切なパラメーターを渡してストアド プロシージャを呼び出します。  
  
## <a name="passing-parameters"></a>パラメーターを渡す  
 通常、データベースで更新しようとしているレコードの値を渡すパラメーターを使用します。  ときに、TableAdapter の`Update`メソッドには、UPDATE ステートメントが実行される、パラメーター値を入力する必要があります。 この値は、該当するデータ コマンドの `Parameters` コレクションから取得します。この場合は TableAdapter の `UpdateCommand` オブジェクトです。  
  
 データ アダプターを生成する Visual Studio tools を使用した場合、`UpdateCommand`オブジェクトには、ステートメント内の各パラメーター プレース ホルダーに対応するパラメーターのコレクションが含まれています。  
  
 各パラメーターの <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> プロパティは、データ テーブル内の列を指しています。 たとえば、`SourceColumn` パラメーターおよび `au_id` パラメーターの `Original_au_id` プロパティには、データ テーブルの author id を含む列が設定されます。ときに、アダプターの`Update`メソッドの実行、作成者 id 列から読み取り、レコードが更新されると、ステートメントに値を設定します。  
  
 UPDATE ステートメントでも、古い (そのレコードは、データベース内にあることができます) の値 (レコードに書き込まれるもの) 両方の新しい値を指定する必要があります。 したがって、それぞれの値に、SET 句のパラメーターと WHERE 句の 2 つのパラメーターがあります。 両方のパラメーターが更新されるレコードからデータを読み取りますが、パラメーターのに基づいて列の値のバージョンを取得[SqlParameter.SourceVersion プロパティ](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx)します。 SET 句のパラメーターは現在のバージョンを取得し、WHERE 句のパラメーターは元のバージョンを取得します。  
  
> [!NOTE]
>  `Parameters` コレクションの値はコードで設定することもできます。通常はデータ アダプターの <xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーで設定します。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [TableAdapter を使用してデータを更新します。](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Visual Studio でのデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)

