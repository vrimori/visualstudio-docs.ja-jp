---
title: "Visual Studio でのデータセットの操作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "キャッシュ [Visual Studio], データセット"
  - "大文字と小文字の区別, データセット"
  - "子レコード"
  - "制約 [Visual Basic], データセット"
  - "現在のレコード (データセットの)"
  - "データ アダプター, データの読み込み (データセットへの)"
  - "データ キャッシュ, データセット"
  - "データ リレーションシップ"
  - "データベース [Visual Basic], 更新"
  - "DataRelation オブジェクト, データセット"
  - "DataSet クラス"
  - "DataSet クラス, データセットの概要"
  - "データセット [Visual Basic]"
  - "データセット [Visual Basic], 拡張プロパティ"
  - "データセット [Visual Basic], 塗りつぶし"
  - "データセット [Visual Basic], msprop"
  - "データセット [Visual Basic], namespace"
  - "データセット [Visual Basic], データの読み込み"
  - "データセット [Visual Basic], リレーションシップ"
  - "拡張プロパティ, 型指定されたデータセットでの"
  - "外部キー, データセット"
  - "マスター/詳細テーブル, データセット"
  - "msprop"
  - "親レコード (データセットの)"
  - "関連テーブル"
  - "関連テーブル, データセット"
  - "リレーションシップ, データセット"
  - "スキーマ [Visual Basic], データセット"
  - "型指定されたデータセット"
  - "型指定されたデータセット, 比較 (型指定されていないデータセットと)"
  - "UNIQUE 制約 (データセット)"
  - "型指定されていないデータセット"
  - "型指定されていないデータセット, 比較 (型指定されたデータセットと)"
  - "更新 (データセットを), データセットの更新の概要"
  - "XML [Visual Basic], データセット"
  - "XML スキーマ, XML スキーマとデータセットの概要"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio でのデータセットの操作
データセットは、アプリケーションで使用するためにデータを一時的に格納できるデータ テーブルを含むオブジェクトです。  アプリケーションでデータを操作する必要がある場合、データをデータセットに読み込むことができ、それがアプリケーションで操作するデータのローカルのメモリ内キャッシュになります。  データセット内のデータは、アプリケーションがデータベースから切断されても操作できます。  データセットでは、データへの変更に関する情報が保持されるので、更新情報を追跡して、アプリケーションがデータベースに再度接続されたときにデータベースに更新情報を送信できます。  
  
 次のトピックでは、Visual Studio でデータセットを操作する方法について詳しく説明します。  
  
|トピック|Description|  
|----------|-----------------|  
|[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)|データセットを作成するためのデザイン時ツールについて説明します。|  
|[方法 : 型指定されたデータセットを作成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデザイン ツールで、型指定されたデータセットを作成する方法を説明します。|  
|[方法 : データセットの機能を拡張する](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|デザイナーで生成されるコード以外のコードを追加するための、データセットの部分クラスを作成する手順を示します。|  
|[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|**ソリューション エクスプローラー**と **\[データ ソース\]** ウィンドウからデータセットを開く方法について説明します。|  
|[方法 : データセットを編集する](../Topic/How%20to:%20Edit%20a%20Dataset.md)|**データセット デザイナー**を使用して、データセット内のオブジェクトを編集する方法を説明します。|  
|[チュートリアル : データセット デザイナーでのデータセットの作成](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|**データ ソース構成**ウィザードを使用せずに、型指定されたデータセットを作成する方法を、段階ごとに説明します。|  
|[DataTable のデザイン](../data-tools/designing-datatables.md)|デザイン時ツールを使用してデータ テーブルの作成と編集を行う方法について説明しているトピックへのリンクを示します。|  
|[データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)|デザイン時ツールを使用してデータ リレーションシップの作成と編集を行う方法について説明しているトピックへのリンクを示します。|  
|[TableAdapter](../Topic/TableAdapters.md)|デザイン時ツールを使用して TableAdapter の作成と編集を行う方法について説明しているトピックへのリンクを示します。|  
|[n 層アプリケーションでのデータセットの操作](../data-tools/work-with-datasets-in-n-tier-applications.md)|n 層アプリケーションと、n 層アプリケーションでデータセットを操作するために使用できる機能について説明します。|  
  
 <xref:System.Data.DataSet> の構造はリレーショナル データベースに似ています。データセットは、テーブル、行、列、制約、およびリレーションシップの階層オブジェクト モデルを公開します。  
  
 データセットには、型指定されたデータセットと型指定されていないデータセットがあります。  詳細については、後の「型指定されたデータセットと型指定されていないデータセット」を参照してください。型指定されたデータセットは、.xsd ファイルからスキーマ \(テーブルと列の構造体\) を派生させるので、プログラミングが簡単です。  アプリケーションでは、型指定されたデータセットと型指定されていないデータセットのどちらでも使用できます。  ただし、型指定されたデータセットを使用した方が、Visual Studio でより多くのツールがサポートされているため、データセットに関するプログラミングが簡単になり、エラーも起こりにくくなります。  
  
 型指定されたデータセットは、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を実行するか、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** で **\[データセット\]** 項目を追加して、作成します。  詳細については、「[方法 : 型指定されたデータセットを作成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)」を参照してください。  
  
 型指定されていないデータセットは、**ツールボックス**から **\[データセット\]** 項目を [Windows Forms Designer](http://msdn.microsoft.com/ja-jp/3c3d61f8-f36c-4d41-b9c3-398376fabb15)または[Component Designer](../Topic/Component%20Designer.md)にドラッグして、作成します。  
  
 データセットを作成したら、[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)で編集します。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 名前空間の次の部分を使用して、型指定されたデータセットと型指定されていないデータセットを作成して操作します。  
  
 ![システム データ データセット名前空間](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
データセットは、System.Data 名前空間内にあります。  
  
 データセットのオブジェクトは、プロパティやコレクションなどの標準的なプログラミング構造によって公開されます。  次に例を示します。  
  
-   <xref:System.Data.DataSet> クラスには、データ テーブルの <xref:System.Data.DataTableCollection> コレクションと <xref:System.Data.DataRelation> オブジェクトの <xref:System.Data.DataRelationCollection> コレクションが格納されます。  
  
-   <xref:System.Data.DataTable> クラスには、テーブルの行の <xref:System.Data.DataRowCollection> コレクション、データ列の <xref:System.Data.DataColumnCollection> コレクション、およびデータ リレーションシップの <xref:System.Data.DataTable.ChildRelations%2A> コレクションと <xref:System.Data.DataTable.ParentRelations%2A> コレクションが格納されます。  
  
-   <xref:System.Data.DataRow> クラスには <xref:System.Data.DataRow.RowState%2A> プロパティが含まれています。このプロパティの値は、データ テーブルがデータベースから最初に読み込まれた後で行が変更されているかどうか、およびどのように変更されているかを示します。  <xref:System.Data.DataRow.RowState%2A> プロパティの値には、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> などがあります。  
  
## データセットへのデータの読み込み  
 既定では、データセットには実際のデータは含まれていません。  データセットにデータを読み込む操作は、実際にはデータセットを構成する個々の <xref:System.Data.DataTable> オブジェクトにデータを読み込む操作を意味します。  TableAdapter クエリを実行するか、またはデータ アダプター \(たとえば、<xref:System.Data.SqlClient.SqlDataAdapter>\) のコマンドを実行して、データ テーブルにデータを読み込みます。  データセットにデータを読み込む場合は、各種のイベントが発生したり、制約が検査されたりします。  データセットへのデータの読み込みの詳細については、「[アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)」を参照してください。  
  
 データセットにデータを読み込むコードは、[ウィンドウ](../Topic/Data%20Sources%20Window.md)から Windows アプリケーションのフォームに項目をドラッグしたときに、フォームのロード イベント ハンドラーに自動的に追加されます。  詳細については、「[チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)」の手順を参照してください。  
  
 TableAdapter を使用してデータセットにデータを読み込む例を次に示します。  
  
 [!CODE [VbRaddataDatasets#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#1)]  
  
 データセットにデータを読み込むにはさまざまな方法があります。  
  
-   データ ウィザードなどのデザイン時ツールを使用してデータセットを作成した場合、TableAdapter の `Fill` メソッドを呼び出してください   \(TableAdapter は、既定の `Fill` メソッドで作成されます。ただし、名前を変更できるため、実際には別の名前になっている場合もあります\)。詳細については、「[方法 : データセットにデータを読み込む](../data-tools/how-to-fill-a-dataset-with-data.md)」の「TableAdapter を使用したデータセットへのデータの読み込み」のセクションを参照してください。  
  
-   <xref:System.Data.Common.DataAdapter> の `Fill` メソッドを呼び出します。  詳細については、「[DataAdapter からの DataSet の読み込み](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)」を参照してください。  
  
-   <xref:System.Data.DataRow> オブジェクトを作成してテーブルの <xref:System.Data.DataRowCollection> コレクションにそれらを追加することにより、データセットのテーブルに手動でデータを読み込みます。  これは実行時にだけ行うことができます。デザイン時には <xref:System.Data.DataRowCollection> コレクションを設定できません。詳細については、「[DataTable へのデータの追加](../Topic/Adding%20Data%20to%20a%20DataTable.md)」を参照してください。  
  
-   XML のドキュメントまたはストリームをデータセットに読み込みます。  詳細については、<xref:System.Data.DataSet.ReadXml%2A> メソッドのトピックを参照してください。  例については、「[チュートリアル : データセットへの XML データの読み込み](../data-tools/read-xml-data-into-a-dataset.md)」を参照してください。  
  
-   他のデータセットの内容をマージ \(コピー\) します。  この方法は、アプリケーションがいくつかの異なるソース \(複数の XML Web サービスなど\) からデータセットを取得し、それを 1 つのデータセットに統合する必要がある場合に便利です。  詳細については、「[DataSet の内容のマージ](../Topic/Merging%20DataSet%20Contents.md)」を参照してください。  
  
-   他の <xref:System.Data.DataTable> の内容をマージ \(コピー\) します。  
  
## データセット内のデータのデータベースへの保存  
 データセット内のレコードが変更された場合は、変更をデータベースにも反映する必要があります。  データセットの変更をデータベースに書き込むには、データセットとその対応するデータベースの間でやり取りを行う TableAdapter または <xref:System.Data.Common.DataAdapter> の `Update` メソッドを呼び出します。  
  
 Visual Studio のデータ デザイン ツールを使用する場合、TableAdapter の Update メソッドを呼び出し、保存するデータ テーブルを渡して、データをデータベースに送信します。  次に例を示します。  
  
 [!CODE [VbRaddataDatasets#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#2)]  
  
 更新処理をより綿密に制御するには、TableAdapter の DBDirect メソッドのいずれかを呼び出すことで、各データ行の個別の値を渡すことができます。  詳細については、「[方法 : TableAdapter を使用してデータを更新する](../data-tools/update-data-by-using-a-tableadapter.md)」および「[チュートリアル : TableAdapter DBDirect メソッドを使用してデータを保存する](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)」を参照してください。  
  
 個別のレコードを操作するために使用される <xref:System.Data.DataRow> クラスには、<xref:System.Data.DataRow.RowState%2A> プロパティが含まれています。このプロパティの値は、データ テーブルがデータベースから最初に読み込まれた後で行が変更されているかどうか、およびどのように変更されているかを示します。  使用できる値は、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、および <xref:System.Data.DataRowState> です。  TableAdapter と <xref:System.Data.Common.DataAdapter> の `Update` メソッドは、<xref:System.Data.DataRow.RowState%2A> プロパティの値を調べて、どのレコードをデータベースに書き込み、どのデータベース コマンド \(`InsertCommand`、`UpdateCommand`、`DeleteCommand`\) を起動するかを決定します。  
  
 データ更新の詳細については、「[データの保存](../data-tools/saving-data.md)」を参照してください。  
  
## データセット内でのレコード間の移動  
 データセットは完全に非接続のデータ コンテナーであるため、ADO レコードセットとは異なり、現在のレコードという概念をサポートしていません。  その代わり、データセット内のすべてのレコードをいつでも使用できます。  
  
 現在のレコードが存在しないため、現在のレコードを指す特定のプロパティはありません。また、レコード間で移動するためのメソッドやプロパティもありません \(後のメモを参照\)。  データセット内の個別のテーブルにはオブジェクトとしてアクセスできます。各テーブルは、行のコレクションを公開します。  このコレクションは他のすべてのコレクションと同じように扱うことができ、コレクションのインデックスによって行にアクセスしたり、プログラミング言語でコレクション固有のステートメントを使用したりできます。  
  
 たとえば、`Customers` テーブルの 4 行目を取得するには、次のようなコードを使用します。  
  
 [!CODE [VbRaddataDatasets#3](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#3)]  
  
> [!NOTE]
>  フォーム内のコントロールをデータセットにバインドする場合、<xref:System.Windows.Forms.BindingNavigator> コンポーネントを使用して、各レコードへのアクセスを簡便化できます。  詳細については、「[方法 : Windows フォームでデータ間を移動する](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md)」を参照してください。  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] を使用すれば、<xref:System.Data.DataSet> オブジェクトのデータを対象に [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) を実行することが可能になります。  詳細については、「[LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)」を参照してください。  
  
## データセットと XML  
 データセットは、XML で表すことができるデータのリレーショナル ビューです。  データセットと XML の間のそのような関係により、データセットでは次のような機能を利用できます。  
  
-   データセットの構造、つまりテーブル、列、リレーションシップ、および制約を XML スキーマ内で定義できます。  構造化された情報を格納しているスキーマに対して、データセットは <xref:System.Data.DataSet.ReadXmlSchema%2A> メソッドと <xref:System.Data.DataSet.WriteXmlSchema%2A> メソッドを使用して読み取りおよび書き込みを行うことができます。  スキーマが存在しない場合、データセットは、リレーショナルに組み立てられる XML ドキュメント内のデータから <xref:System.Data.DataSet.InferXmlSchema%2A> メソッドを使用してスキーマを推論できます。  XML のスキーマの詳細については、「[XML スキーマの作成](../Topic/Building%20XML%20Schemas.md)」を参照してください。  
  
-   データセット クラスを作成して、データ構造体を定義するスキーマ情報を取り込むことができます。  これを*型指定された*データセットと呼びます。  型指定されたデータセットを作成する方法については、「[方法 : 型指定されたデータセットを作成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)」を参照してください。  
  
-   データセットの <xref:System.Data.DataSet.ReadXml%2A> メソッドを使用して、XML のドキュメントやストリームをデータセットに読み込むことができます。また、データセットの <xref:System.Data.DataSet.WriteXml%2A> メソッドを使用して、データセットを XML として書き出すこともできます。  XML はアプリケーション間でデータを交換するための標準形式であるため、これにより、ほかのアプリケーションから送信された XML 形式の情報をデータセットに読み込むことができます。  同様に、データセットのデータを XML のストリームまたはドキュメントとして書き出すことにより、ほかのアプリケーションとデータを共有したり、単に標準形式で保存したりできます。  
  
-   データセットまたはデータ テーブルの内容の XML ビュー \(<xref:System.Xml.XmlDataDocument> オブジェクト\) を作成し、リレーショナル メソッド \(データセットによる\) または XML メソッドのいずれかを使用して、データを表示および操作できます。  2 つのビューは、変更されるたびに自動的に同期をとります。  
  
## 型指定されたデータセットと型指定されていないデータセット  
 型指定されたデータセットは、まず基本 <xref:System.Data.DataSet> クラスから派生し、次に**データセット デザイナー**の情報を使用して生成されるデータセットです。この情報は .xsd ファイルに格納されており、厳密に型指定された新しいデータセット クラスの生成に使用されます。  スキーマの情報 \(テーブルや列など\) は、新しいデータセット クラスの最上位のオブジェクトとプロパティとして生成され、組み込まれます。  型指定されたデータセットは、基本の <xref:System.Data.DataSet> クラスから継承するため、型指定されたクラスでは、<xref:System.Data.DataSet> クラスのすべての機能を使用できます。また、<xref:System.Data.DataSet> クラスのインスタンスをパラメーターとして取るメソッドで使用できます。  
  
 対照的に、型指定されていないデータセットには対応する組み込みスキーマがありません。  型指定されたデータセットと同様に、型指定されていないデータセットにもテーブルや列などが含まれますが、それはコレクションとしてだけ公開されます。  ただし、型指定されていないデータセット内にテーブルなどのデータ要素を手動で作成した後で、データセットの <xref:System.Data.DataSet.WriteXmlSchema%2A> メソッドを使用してデータセットの構造をスキーマとしてエクスポートできます。  
  
### 型指定されたデータセットと型指定されていないデータセットにおけるデータ アクセスの比較  
 型指定されたデータセットのクラスには、オブジェクト モデルが格納されます。このオブジェクト モデルには、テーブルと列の実際の名前を値として格納するプロパティが格納されます。  たとえば、型指定されたデータセットで作業している場合は、次に示すコードを使用して列を参照できます。  
  
 [!CODE [VbRaddataDatasets#4](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#4)]  
  
 一方、型指定されていないデータセットで作業している場合は、次に示すコードを使用します。  
  
 [!CODE [VbRaddataDatasets#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#5)]  
  
 型付きアクセスの方が読みやすいだけでなく、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **コード エディター**の IntelliSense によって完全にサポートされています。  扱いやすさに加えて、型指定されたデータセットの構文ではコンパイル時に型チェックが行われるため、データセット メンバーに値を割り当てる場合にエラーの発生する可能性が低くなります。  <xref:System.Data.DataSet> 内の列の名前を変更して、アプリケーションをコンパイルすると、ビルド エラーが発生します。  **\[タスク一覧\]** 内のビルド エラーをダブルクリックすると、変更前の列名を参照するコード行に直接移動できます。  実行時のテーブルや列へのアクセスも、型指定されたデータセットの方が少し速くなります。これは、アクセスが実行時にコレクションを通して決定される代わりに、コンパイル時に決定されるためです。  
  
 型指定されたデータセットには多くの利点がありますが、型指定されていないデータセットを使用すると便利な状況も各種あります。  最も明らかな状況は、データセットに対して使用できるスキーマがない場合です。  この状況は、たとえば、アプリケーションがデータセットを返すコンポーネントとやり取りするときに、その構造が事前にわかっていない場合に生じます。  同様に、操作対象のデータが予測可能な静的構造を持っていない場合もあります。そのような場合、型指定されたデータセットを使用するのは実用的ではありません。なぜなら、データ構造が変更されるたびに型指定されたデータセット クラスを再生成する必要があるためです。  
  
 より一般的には、使用可能なスキーマなしでデータセットを動的に作成する場合が多くあります。  そのような場合、リレーショナル方法でデータを表すことができる限り、データセットは単に情報を保持することができる便利な構造です。  同時に、ほかのプロセスに渡すために情報をシリアル化したり XML ファイルに書き出したりするデータセットの機能も利用できます。  
  
## データセットにおける大文字と小文字の区別  
 データセット内のテーブル名や列名は、既定で大文字と小文字が区別されません。つまり、データセット内の "Customers" というテーブルは、"customers" という形でも参照できます。これは、SQL Server の既定の動作などの多くのデータベースにおける名前付け規則に対応しています。これらのデータベースでは、データ要素の名前を大文字と小文字の違いだけでは区別できません。  
  
> [!NOTE]
>  データセットとは異なり、XML ドキュメントでは大文字と小文字が区別されるため、スキーマで定義するデータ要素の名前では大文字と小文字が区別されます。  たとえば、スキーマ プロトコルでは、同じスキーマで "Customers" という名前のテーブルと "customers" という名前の別のテーブルを定義できます。そのため、大文字と小文字の違いしかない要素を含むスキーマを使用してデータセット クラスを生成すると、名前が競合することがあります。  
  
 ただし、データセット内でデータを解釈するときに、大文字と小文字の区別が考慮される場合もあります。  たとえば、データセット テーブル内のデータにフィルターをかける場合には、検索条件との比較で大文字と小文字を区別するかどうかによって異なる結果が返されることがあります。  フィルター処理、検索、および並べ替えにおける大文字と小文字の区別は、データセットの <xref:System.Data.DataSet.CaseSensitive%2A> プロパティを設定することによって制御できます。  データセット内のすべてのテーブルは、このプロパティの値を既定で継承します。  各テーブルについてこのプロパティをオーバーライドするには、そのテーブルの <xref:System.Data.DataTable.CaseSensitive%2A> プロパティを設定します。  
  
## 関連するテーブルと DataRelation オブジェクト  
 データセットに複数のテーブルが含まれる場合は、テーブル間に情報のリレーションシップが存在する可能性があります。  データセットには本質的にそのようなリレーションシップについての情報は含まれていません。したがって、関連し合うテーブル内のデータを操作する場合には、データセット内のテーブル間のリレーションシップを記述する <xref:System.Data.DataRelation> オブジェクトを作成します。  詳細については、「[方法 : 関連する DataTable のレコードにアクセスする](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)」を参照してください。  <xref:System.Data.DataRelation> オブジェクトを使用することにより、親レコードに関連する子レコードおよび子レコードに関連する親レコードをプログラムでフェッチできます。  詳細については、「[データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)」を参照してください。  データベースに複数のテーブル間のリレーションシップが格納されている場合、デザイン ツールによって <xref:System.Data.DataRelation> オブジェクトが自動作成されます。  
  
 たとえば、Northwind というデータベースに顧客データと注文データが含まれるとします。  `Customers` テーブルには、次のようなレコードが含まれています。  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 データセットには、注文情報を含む別のテーブルも含まれています。  この `Orders` テーブルには、顧客 ID が外部キー列として含まれています。  `Orders` テーブルの一部の列だけを選択すると、次のようになります。  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 各顧客が複数の注文を行う場合があるため、顧客と注文の間には一対多リレーションシップがあります。  たとえば、上のテーブルでは、ALFKI という顧客からの注文が 2 つあります。  
  
 <xref:System.Data.DataRelation> オブジェクトを使用して、子テーブルまたは親テーブルから関連するレコードを取得できます。  たとえば、ANTON という顧客を記述したレコードを操作しているときに、この顧客の注文を記述したレコードのコレクションを取得できます。  詳細については、「<xref:System.Data.DataRow.GetChildRows%2A>」を参照してください。  同様に、OrderId 10507 を表すレコードを操作しているときに、リレーションシップ オブジェクトをたどって、親 ANTON に対するレコードを取得できます。  詳細については、「<xref:System.Data.DataRow.GetParentRow%2A>」を参照してください。  
  
## 制約  
 ほとんどのデータベースと同様に、データセットはデータの整合性を保証する手段として制約をサポートしています。  制約は、テーブルの行を挿入、更新、または削除するときに適用される規則です。  2 つの種類の制約を定義できます。  
  
-   列の新しい値がテーブル内で重複しないことをチェックする *UNIQUE* 制約。  
  
-   マスター テーブル内のレコードが更新または削除されるときに関連する子レコードをどのように更新するかの規則を定義する*外部キー*の制約。  たとえば、子レコードが作成される前に、外部キーの制約により親レコードの存在を確認します。  
  
 データセットでは、制約に個別のテーブル \(外部キーの制約の場合\) または列 \(列の値が重複しないことを保証する UNIQUE 制約の場合\) が関連付けられます。  制約は、<xref:System.Data.UniqueConstraint> 型または <xref:System.Data.ForeignKeyConstraint> 型のオブジェクトとして実装されます。  これらの制約は、<xref:System.Data.DataTable> の <xref:System.Data.DataTable.Constraints%2A> コレクションに追加されます。  また、<xref:System.Data.DataColumn> の <xref:System.Data.DataColumn.Unique%2A> プロパティを `true` に設定するだけでも、UNIQUE 制約を指定できます。  
  
 データセット自体は、制約が適用されるかどうかを指定するブール型の <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティをサポートしています。  既定では、このプロパティは `true` に設定されます。  ただし、制約を一時的にオフにすると便利な場合もあります。  最も一般的な例は、レコードの変更によって一時的に無効な状態が発生するような場合です。  そのような場合は、変更を完了して \(それによって有効な状態に戻って\) から、制約を再び有効にできます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、データセットを定義するときに制約が暗黙に作成されます。  データセットに主キーを追加すると、その主キー列に対して UNIQUE 制約が暗黙に作成されます。  それ以外の列に UNIQUE 制約を指定するには、その列の <xref:System.Data.DataColumn.Unique%2A> プロパティを `true` に設定します。  
  
 外部キーの制約を作成するには、データセット内に <xref:System.Data.DataRelation> オブジェクトを作成します。  <xref:System.Data.DataRelation> オブジェクトを使用すると、関連するレコードに関する情報をプログラムで取得できるだけでなく、外部キーの制約の規則を定義できます。  
  
## データセットの拡張プロパティ  
 拡張プロパティは、.xsd ファイルからデータセットを生成する際に名前の競合が発生した場合に、名前のマッピングを提供します。  .xsd ファイル内の識別子が、データセットの生成元によって作成された名前と異なる場合、`msprop` 名前空間でそのデータセットに拡張プロパティが追加されます。  生成される可能性のある拡張プロパティを以下の表に示します。  
  
|Object|拡張プロパティ|  
|------------|-------------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## 参照  
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)