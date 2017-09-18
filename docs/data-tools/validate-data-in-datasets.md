---
title: "データセットのデータの検証 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データの妥当性検査"
  - "データの妥当性検査, データセット"
  - "更新 (データセットを), 検証 (データを)"
  - "検証 (データを), データセット"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# データセットのデータの検証
データの妥当性検査は、データ オブジェクトに入力する値が、データセットのスキーマ内の制約、およびアプリケーションに対して設定されている規則に従っていることを確認するプロセスです。  基になるデータベースに更新を送信する前にデータを検証すると、エラーの発生数、およびアプリケーションとデータベースの間で生じる可能性のあるラウンド トリップの回数を減らすことができます。  データセットに書き込まれるデータが有効であることを確認するには、データセット自体に有効性の確認を組み込みます。  データセットの更新がフォームのコントロールで直接実行される場合、コンポーネント内で実行される場合、またはその他の方法で実行される場合も、データセットはデータを確認できます。  データセットはアプリケーションの一部であるため、データベースのバック エンドに同様のチェックを組み込むのとは異なりアプリケーション固有の確認を組み込むことができる論理的な場所です。  
  
 アプリケーションに検証を追加する場所として推奨されるのは、データセットの部分クラス ファイルです。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] または [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] で**データセット デザイナー**を開き、検証を作成する列またはテーブルをダブルクリックします。  この操作で、<xref:System.Data.DataTable.ColumnChanging> イベント ハンドラーまたは <xref:System.Data.DataTable.RowChanging> イベント ハンドラーが自動的に作成されます。  詳細については、「[方法 : 列の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)」または「[方法 : 行の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)」を参照してください。  コード例全体については、「[チュートリアル : データセットへの検証の追加](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md)」を参照してください。  
  
## データの検証  
 データセット内での検証は次のようにして行われます。  
  
-   個々のデータ列内の値を変更しているときにデータをチェックできるアプリケーション固有の検証を作成する。  詳細については、「[方法 : 列の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)」を参照してください。  
  
-   データ行全体を変更する際に、値を変更しているときにデータをチェックできるアプリケーション固有の検証を作成する。  詳細については、「[方法 : 行の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)」を参照してください。  
  
-   キー制約や一意の制約などをデータセットの実際のスキーマ定義の一部として作成する。  スキーマ定義に検証を組み込む方法の詳細については、[一意の値が格納されるように DataColumn を制約する](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint)を参照してください。  
  
-   <xref:System.Data.DataColumn.MaxLength%2A>、<xref:System.Data.DataColumn.AllowDBNull%2A>、<xref:System.Data.DataColumn.Unique%2A> などの <xref:System.Data.DataColumn> オブジェクトのプロパティを設定する。  
  
 レコード内で変更が発生すると、<xref:System.Data.DataTable> オブジェクトは次のイベントを発生させます。  
  
-   <xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.ColumnChanged> イベントは、各列への個別の変更の実行中と実行後に発生します。  <xref:System.Data.DataTable.ColumnChanging> イベントは、特定の列の変更を検証する場合に役立ちます。  提案された変更に関する情報はイベントにより引数として渡されます。  詳細については、「[方法 : 列の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)」を参照してください。  
  
-   <xref:System.Data.DataTable.RowChanging> イベントおよび <xref:System.Data.DataTable.RowChanged> イベントは、行の変更の実行中および実行後に発生します。  <xref:System.Data.DataTable.RowChanging> イベントは、変更が行のどこかで発生していることを単に示すという点でより汎用的です。変更された列は特定できません。  詳細については、「[方法 : 行の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)」を参照してください。  
  
 つまり、列への変更は既定でそれぞれ 4 つのイベントを発生させます。最初に変更される特定の列に対する <xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.ColumnChanged> イベント、次に <xref:System.Data.DataTable.RowChanging> イベントおよび <xref:System.Data.DataTable.RowChanged> イベントです。  行に複数の変更が行われる場合、イベントは各変更に対して発生します。  
  
> [!NOTE]
>  個々の列の変更が完了すると、データ行の <xref:System.Data.DataRow.BeginEdit%2A> メソッドが <xref:System.Data.DataTable.RowChanging> イベントと <xref:System.Data.DataTable.RowChanged> イベントをオフにします。  その場合は、<xref:System.Data.DataTable.RowChanging> イベントおよび <xref:System.Data.DataTable.RowChanged> イベントが一度しか発生しなければ、イベントは <xref:System.Data.DataRow.EndEdit%2A> メソッドが呼び出されるまで発生しません。  詳細については、「[方法 : データセットの読み込み中に制約をオフにする](../data-tools/turn-off-constraints-while-filling-a-dataset.md)」を参照してください。  
  
 イベントの選択は、構築する検証の精度によって異なります。  列の変更直後にエラーを検出することが必要な場合は、<xref:System.Data.DataTable.ColumnChanging> イベントを使って検証を構築します。  そうでない場合は、一度に複数のエラーを検出できる <xref:System.Data.DataTable.RowChanging> イベントを使用します。  さらに、1 つの列の値が別の列の内容に基づいて検証されるような方法でデータが構築されている場合は、<xref:System.Data.DataTable.RowChanging> イベント中に検証を実行する必要があります。  
  
 レコードを更新すると、変更の実行中および実行後に応答できるイベントが <xref:System.Data.DataTable> オブジェクトによって生成されます。  
  
 アプリケーションが型指定されたデータセットを使用している場合は、厳密に型指定されたイベント ハンドラーを作成できます。  これにより、4 つの別の型指定されたイベント \(`dataTableNameRowChanging`、`dataTableNameRowChanged`、`dataTableNameRowDeleting`、および `dataTableNameRowDeleted`\) が追加され、これに対してハンドラーを作成できます。  これらの型指定されたイベント ハンドラーはテーブルの列名を含む引数を渡すため、コードの読み書きが簡単になります。  
  
## データ更新イベント  
  
|イベント|説明|  
|----------|--------|  
|<xref:System.Data.DataTable.ColumnChanging>|列の値は変更されます。  イベントは、提案された新しい値と共に行および列を渡します。|  
|<xref:System.Data.DataTable.ColumnChanged>|列の値は変更されました。  イベントは、提案された値と共に行および列を渡します。|  
|<xref:System.Data.DataTable.RowChanging>|<xref:System.Data.DataRow> オブジェクトに対する変更が、これからデータセットにコミットされるところです。  まだ <xref:System.Data.DataRow.BeginEdit%2A> メソッドを呼び出していない場合は、<xref:System.Data.DataTable.ColumnChanging> イベントの発生直後に列へのそれぞれの変更に対する <xref:System.Data.DataTable.RowChanging> イベントが発生します。  変更前に <xref:System.Data.DataRow.BeginEdit%2A> を呼び出した場合は、<xref:System.Data.DataRow.EndEdit%2A> メソッドを呼び出したときにだけ <xref:System.Data.DataTable.RowChanging> イベントが発生します。<br /><br /> このイベントは、実行されるアクションの種類 \(変更、挿入など\) を示す値と共に行を渡します。|  
|<xref:System.Data.DataTable.RowChanged>|行は変更されました。  このイベントは、実行されるアクションの種類 \(変更、挿入など\) を示す値と共に行を渡します。|  
|<xref:System.Data.DataTable.RowDeleting>|行は削除されます。  このイベントは、実行されるアクションの種類 \(削除\) を示す値と共に行を渡します。|  
|<xref:System.Data.DataTable.RowDeleted>|行は削除されました。  このイベントは、実行されるアクションの種類 \(削除\) を示す値と共に行を渡します。|  
  
 <xref:System.Data.DataTable.ColumnChanging>、<xref:System.Data.DataTable.RowChanging>、および <xref:System.Data.DataTable.RowDeleting> の各イベントは、更新処理中に発生します。  これらのイベントを使用してデータを検証したり、ほかの種類の処理を実行したりできます。  これらのイベント中は更新の処理の実行中であるため、例外のスローによって更新をキャンセルし、変更が完了しないようにできます。  
  
 <xref:System.Data.DataTable.ColumnChanged>、<xref:System.Data.DataTable.RowChanged>、および <xref:System.Data.DataTable.RowDeleted> の各イベントは、更新が正常に完了した場合に発生する通知イベントです。  これらのイベントは、正常な更新に応じてさらに次のアクションを行うときに役立ちます。  
  
## 参照  
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータを検証する](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)