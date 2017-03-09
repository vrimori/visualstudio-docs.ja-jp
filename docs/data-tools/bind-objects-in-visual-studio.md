---
title: "Visual Studio におけるオブジェクトのバインド | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "バインド, オブジェクトへの"
  - "データ [Visual Studio], バインド (オブジェクトに)"
  - "データ [Visual Studio], オブジェクトのバインディング"
  - "オブジェクトのバインディング"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio におけるオブジェクトのバインド
Visual Studio には、エンティティ、データセット、サービスなどのデータ ソースではなく、カスタム オブジェクトをアプリケーションでデータ ソースとして使用するためのデザイン時ツールが用意されています。  
  
## オブジェクトの要件  
 Visual Studio のデータ デザイン ツールでカスタム オブジェクトを使用するために必要な唯一の要件は、オブジェクトに少なくとも 1 つのパブリック プロパティが必要であることです。  
  
 一般に、カスタム オブジェクトをアプリケーションのデータ ソースとして機能させるために、特定のインターフェイス、コンストラクター、または属性を実装する必要はありません。  ただし、オブジェクトを **\[データ ソース\]** ウィンドウからデザイン サーフェイスにドラッグしてデータ バインド コントロールを作成する場合、およびオブジェクトが <xref:System.ComponentModel.ITypedList> インターフェイスまたは <xref:System.ComponentModel.IListSource> インターフェイスを実装する場合、そのオブジェクトの既定のコンストラクター \(パラメーターなしのコンストラクター\) が必要です。  それ以外の場合、Visual Studio ではデータ ソース オブジェクトをインスタンス化できず、項目をデザイン サーフェイスにドラッグしたときにエラーが表示されます。  
  
## カスタム オブジェクトのデータ ソースとしての使用例  
 オブジェクトをデータ ソースとして使用する際にアプリケーション ロジックを実装する方法は多数ありますが、Visual Studio が生成する [TableAdapter](../data-tools/tableadapter-overview.md) オブジェクトを使用することで、いくつかの標準的な操作を簡素化できます。  このページでは、TableAdapter を使用して標準的なプロセスを実装する方法について説明しますが、カスタム オブジェクトを作成するためのガイドは意図していません。  たとえば、オブジェクトまたはアプリケーションのロジックの実装にかかわらず、一般に次の標準的な操作を実行できます。  
  
-   オブジェクトにデータを読み込む \(通常はデータベースから\)。  
  
-   型指定されたオブジェクトのコレクションを作成する。  
  
-   オブジェクトをコレクションに追加、およびコレクションから削除する。  
  
-   フォーム上でオブジェクト データをユーザーに表示する。  
  
-   オブジェクトのデータを変更または編集する。  
  
-   オブジェクトからデータベースにデータを戻して保存する。  
  
> [!NOTE]
>  このページの例をより良く理解するために、「[チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)」を完了することをお勧めします。  このチュートリアルでは、このヘルプ ページで説明するオブジェクトを作成します。  
  
### オブジェクトへのデータの読み込み  
 この例では、TableAdapter を使用してオブジェクトにデータを読み込みます。  既定では、TableAdapter はデータベースからデータを取得するメソッドとデータ テーブルにデータを設定するメソッドの 2 種類のメソッドで作成されます。  
  
-   `TableAdapter.Fill` メソッドは、返されたデータを既存のデータ テーブルに読み込みます。  
  
-   `TableAdapter.GetData` メソッドは、データを読み込んだ新しいデータ テーブルを返します。  
  
 カスタム オブジェクトにデータを最も簡単に読み込む方法は `TableAdapter.GetData` メソッドを呼び出し、返されたデータ テーブルの行のコレクションを反復処理し、各オブジェクトに各行の値を設定することです。  TableAdapter に追加されたクエリにデータ入力されたデータ テーブルを返す `GetData` メソッドを作成できます。  
  
> [!NOTE]
>  Visual Studio は既定で TableAdapter のクエリに `Fill` と `GetData` という名前を付けていますが、この名前は任意の有効なメソッド名に変更できます。  
  
 データ テーブルの行を反復処理し、オブジェクトにデータを設定する方法の例を次に示します。  
  
 完全なコード例については、「[チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)」を参照してください。  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### 型指定されたオブジェクトのコレクションの作成  
 オブジェクトにはコレクションのクラスを作成するか、または [BindingSource コンポーネント](../Topic/BindingSource%20Component.md) が自動的に提供する型指定されたコレクションを使用できます。  
  
 オブジェクトのためにカスタムのコレクション クラスを作成する場合は、<xref:System.ComponentModel.BindingList%601> から継承することをお勧めします。  このジェネリック クラスは、Windows フォームのデータ バインド インフラストラクチャに通知を送信するイベントを発生する機能と共にコレクションを管理するための機能を提供します。  
  
 <xref:System.Windows.Forms.BindingSource> で自動生成されるコレクションは、型指定されたコレクションに <xref:System.ComponentModel.BindingList%601> を使用します。  アプリケーションが追加機能を必要としない場合は、<xref:System.Windows.Forms.BindingSource> 内でコレクションを維持できます。  詳細については、<xref:System.Windows.Forms.BindingSource> クラスの <xref:System.Windows.Forms.BindingSource.List%2A> プロパティを参照してください。  
  
> [!NOTE]
>  コレクションが <xref:System.ComponentModel.BindingList%601> の基本実装が提供していない機能を必要とする場合は、必要に応じてカスタム コレクションを作成してクラスに追加する必要があります。  
  
 `Order` オブジェクトの厳密に型指定されたコレクションのクラスを作成する方法のコード例を次に示します。  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### コレクションへのオブジェクトの追加  
 オブジェクトをコレクションに追加する場合は、カスタム コレクション クラスまたは <xref:System.Windows.Forms.BindingSource> の `Add` メソッドを呼び出します。  
  
 <xref:System.Windows.Forms.BindingSource> を使用してコレクションを追加する例については、「[チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)」の `LoadCustomers` メソッドを参照してください。  
  
 オブジェクトをカスタム コレクションを追加する例については、「[チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)」の `LoadOrders` メソッドを参照してください。  
  
> [!NOTE]
>  <xref:System.ComponentModel.BindingList%601> から継承する場合、`Add` メソッドは自動的にカスタム コレクションに提供されます。  
  
 <xref:System.Windows.Forms.BindingSource> の型指定されたコレクションにオブジェクトを追加する方法のコード例を次に示します。  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 <xref:System.ComponentModel.BindingList%601> から継承された型指定されたコレクションにオブジェクトを追加する方法のコード例を次に示します。  
  
> [!NOTE]
>  この例では、`Orders` コレクションは `Customer` オブジェクトのプロパティです。  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### コレクションからのオブジェクトの削除  
 コレクションからオブジェクトを削除する場合は、カスタム コレクション クラスまたは <xref:System.Windows.Forms.BindingSource> の `Remove` メソッドまたは `RemoveAt` メソッドを呼び出します。  
  
> [!NOTE]
>  `Remove` メソッドと `RemoveAt` メソッドは、<xref:System.ComponentModel.BindingList%601> から継承する際にカスタム コレクションに自動的に提供されます。  
  
 <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> メソッドを使用して <xref:System.Windows.Forms.BindingSource> の型指定されたコレクションからオブジェクトを探して削除する方法のコード例を次に示します。  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### ユーザーへのオブジェクト データの表示  
 オブジェクトのデータをユーザーに表示するには、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png) を使用してオブジェクト データ ソースを作成し、次に **\[データ ソース\]** ウィンドウからフォームにオブジェクト全体または個々のプロパティをドラッグします。  
  
 オブジェクト データ ソースの作成の詳細については、「[方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)」を参照してください。  
  
 オブジェクトから Windows フォームへのデータの表示の詳細については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。  
  
### オブジェクトのデータの変更  
 Windows フォーム コントロールにデータ バインドされたカスタム オブジェクトのデータを編集するには、単にバインドされたコントロールのデータを編集するか、またはオブジェクトのプロパティを直接編集します。  データ バインディング アーキテクチャがオブジェクトのデータを更新します。  
  
 アプリケーションで変更内容を追跡し、指定した変更を元の値にロールバックする必要がある場合は、オブジェクト モデルにこの機能を実装する必要があります。  データ テーブルで指定した変更内容を追跡する方法の例については、「<xref:System.Data.DataRowState>」、「<xref:System.Data.DataSet.HasChanges%2A>」、および「<xref:System.Data.DataTable.GetChanges%2A>」を参照してください。  
  
### オブジェクトのデータをデータベースに戻して保存する  
 オブジェクトのデータは、オブジェクトから値を TableAdapter の DBDirect のメソッドに渡すことによってデータベースに戻して保存します。  
  
 Visual Studio は、データベースに対して直接実行できる DBDirect のメソッドを作成します。  この一連のメソッドは、DataSet オブジェクトや DataTable オブジェクトを必要としません。  
  
|TableAdapter DBDirect のメソッド|Description|  
|---------------------------------|-----------------|  
|`TableAdapter.Insert`|個々の列値をメソッド パラメーターとして渡して、新しいレコードをデータベースに追加します。|  
|`TableAdapter.Update`|データベースの既存のレコードを更新します。  Update メソッドは、元の列値と新しい列値をメソッド パラメーターとして受け取ります。  元の値は元のレコードを探すために使用し、新しい値はレコードを更新するために使用します。<br /><br /> `TableAdapter.Update` メソッドも <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow>、または <xref:System.Data.DataRow> の配列をメソッド パラメーターとして受け取って、データセットの変更内容をデータベースに反映して戻すために使用します。|  
|`TableAdapter.Delete`|メソッド パラメーターとして渡された元の列値に基づいてデータベースから既存のレコードを削除します。|  
  
 オブジェクトのコレクションからデータを保存するには、for\-next ループなどを使用してオブジェクトのコレクションを反復処理し、TableAdapter の DBDirect のメソッドを使用して各オブジェクトの値をデータベースに送ります。  
  
 `TableAdapter.Insert` DBDirect メソッドを使用して、新しい顧客を直接データベースに追加する方法の例を次に示します。  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## 参照  
 [方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [方法 : オブジェクトからデータベースにデータを保存する](../data-tools/save-data-from-an-object-to-a-database.md)   
 [方法 : TableAdapter で直接データベースにアクセスする](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [チュートリアル : TableAdapter DBDirect メソッドを使用してデータを保存する](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [データの保存](../data-tools/saving-data.md)