---
title: "Walkthrough: Customizing the Insert, Update, and Delete Behavior of Entity Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Customizing the Insert, Update, and Delete Behavior of Entity Classes
[Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) は、データベース内のオブジェクトに基づく [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラス \(エンティティ クラス\) を作成および編集するためのビジュアル デザイン サーフェイスを提供します。[LINQ to SQL](../Topic/LINQ%20to%20SQL.md) を使用すると、LINQ テクノロジを使用して SQL データベースにアクセスできます。詳細については、「[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)」を参照してください。  
  
 既定では、更新を実行するロジックは [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムによって提供されます。ランタイムは、テーブルのスキーマ \(列定義と主キー情報\) に基づいて、既定の Insert、Update、および Delete の各ステートメントを作成します。既定の動作を使用しない場合は、更新動作を構成し、データベースのデータの操作に必要な Insert、Update、および Delete を実行する特定のストアド プロシージャを指定できます。この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。また、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。詳細については、「[Customizing Operations By Using Stored Procedures](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md)」を参照してください。  
  
> [!NOTE]
>  このチュートリアルでは、Northwind データベースで **InsertCustomer**、**UpdateCustomer**、および **DeleteCustomer** の各ストアド プロシージャを使用できるようにしておく必要があります。これらのストアド プロシージャの作成方法の詳細については、「[チュートリアル: Northwind の Customers テーブル用 Update ストアド プロシージャの作成](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)」を参照してください。  
  
 このチュートリアルでは、ストアド プロシージャを使用して、データベースにデータを保存する既定の LINQ to SQL ランタイムの動作をオーバーライドするために必要な手順を示します。  
  
 このチュートリアルでは、次のタスクを実行する方法を学習します。  
  
-   新しい Windows フォーム アプリケーションを作成し、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ファイルを追加します。  
  
-   Northwind の Customers テーブルにマップされるエンティティ クラスを作成します。  
  
-   LINQ to SQL Customer クラスを参照するオブジェクト データ ソースを作成します。  
  
-   Customer クラスにバインドされる <xref:System.Windows.Forms.DataGridView> を含む Windows フォームを作成します。  
  
-   フォームの保存機能を実装します。  
  
-   [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にストアド プロシージャを追加することにより、<xref:System.Data.Linq.DataContext> のメソッドを作成します。  
  
-   ストアド プロシージャを使用して挿入、更新、および削除を実行するように Customer クラスを構成します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、次の条件が必要です。  
  
-   Northwind サンプル データベースの SQL Server バージョンにアクセスします。詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
-   Northwind データベースに **InsertCustomer**、**UpdateCustomer**、および **DeleteCustomer** の各ストアド プロシージャが必要です。詳細については、「[チュートリアル: Northwind の Customers テーブル用 Update ストアド プロシージャの作成](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)」を参照してください。  
  
## アプリケーションの作成と LINQ to SQL クラスの追加  
 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスを操作してデータを Windows フォームに表示できるように、新しい Windows フォーム アプリケーションを作成し、LINQ to SQL クラス ファイルを追加します。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### LINQ to SQL クラスを含む新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに「UpdatingwithSProcsWalkthrough」という名前を付けます。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]は [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトと C\# プロジェクトでサポートされています。したがって、新しいプロジェクトはこれらの言語のどちらかで作成してください。  
  
3.  **\[Windows フォーム アプリケーション\]** テンプレートをクリックし、**\[OK\]** をクリックします。詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     UpdatingwithSProcsWalkthrough プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
4.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
5.  **\[LINQ to SQL クラス\]** テンプレートをクリックし、**\[名前\]** ボックスに「Northwind.dbml」と入力します。  
  
6.  **\[追加\]** をクリックします。  
  
     プロジェクトに空の LINQ to SQL クラス ファイル \(Northwind.dbml\) が追加され、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]が開きます。  
  
## Customer エンティティ クラスとオブジェクト データ ソースの作成  
 **サーバー エクスプローラー**または**データベース エクスプローラー**から [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にテーブルをドラッグして、データベース テーブルにマップされた [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスを作成します。結果は、データベース内のテーブルにマップされた LINQ to SQL エンティティ クラスになります。作成したエンティティ クラスは、パブリック プロパティを持つ他のクラスと同様に、オブジェクト データ ソースとして使用できます。  
  
#### Customer エンティティ クラスを作成し、そのエンティティ クラスでデータ ソースを構成するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、SQL Server バージョンの Northwind サンプル データベース上の Customer テーブルを探します。詳細については、「[方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)」を参照してください。  
  
2.  **サーバー エクスプローラー**または**データベース エクスプローラー**から [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] サーフェイスに **\[Customers\]** ノードをドラッグします。  
  
     **Customer** という名前のエンティティ クラスが作成されます。これには、Customers テーブルの列に対応するプロパティが含まれています。このエンティティ クラスは Customers テーブルの 1 人の顧客を表すため、**Customers** ではなく **Customer** という名前が付けられます。  
  
    > [!NOTE]
    >  このような名前の変更動作を*複数形化*と呼びます。これは [\[オプション\] ダイアログ ボックス](../Topic/Options%20Dialog%20Box%20\(Visual%20Studio\).md) でオンまたはオフにできます。詳細については、「[How to: Turn Pluralization On and Off \(O\/R Designer\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)」を参照してください。  
  
3.  **\[ビルド\]** メニューの **\[UpdatingwithSProcsWalkthrough のビルド\]** をクリックして、プロジェクトをビルドします。  
  
4.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
5.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックします。  
  
6.  **\[データソースの種類を選択\]** ページで、**\[オブジェクト\]** をクリックし、**\[次へ\]** をクリックします。  
  
7.  **\[UpdatingwithSProcsWalkthrough\]** ノードを展開し、**\[Customer\]** クラスを探して選択します。  
  
    > [!NOTE]
    >  **Customer** クラスが使用可能でない場合は、ウィザードをキャンセルし、プロジェクトをビルドしてからウィザードを再実行します。  
  
8.  **\[完了\]** をクリックしてデータ ソースを作成し、**Customer** エンティティ クラスを **\[データ ソース\]** ウィンドウに追加します。  
  
## Windows フォームに顧客データを表示するための DataGridView の作成  
 **\[データ ソース\]** ウィンドウから Windows フォームに [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] データ ソース項目をドラッグして、エンティティ クラスにバインドされるコントロールを作成します。  
  
#### エンティティ クラスにバインドされるコントロールを追加するには  
  
1.  デザイン ビューで \[Form1\] を開きます。  
  
2.  **\[データ ソース\]** ウィンドウから \[Form1\] に **\[Customer\]** ノードをドラッグします。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウを表示するには、**\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
3.  コード エディターで \[Form1\] を開きます。  
  
4.  フォームに次のコードを追加します。フォームに対してグローバルになるように、Form1 クラスの内部でありながら、どのメソッドにも属さない位置に追加します。  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  `Form_Load` イベントのイベント ハンドラーを作成し、ハンドラーに次のコードを追加します。  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## 保存機能の実装  
 既定では、保存ボタンが有効ではなく、保存機能は実装されていません。また、オブジェクト データ ソースに対してデータ バインド コントロールを作成しても、変更されたデータをデータベースに保存するコードは自動的には追加されません。ここでは、保存ボタンを有効にし、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] オブジェクトの保存機能を実装する方法について説明します。  
  
#### 保存機能を実装するには  
  
1.  デザイン ビューで \[Form1\] を開きます。  
  
2.  **CustomerBindingNavigator** の保存ボタン \(フロッピー ディスクのアイコンのボタン\) を選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[Enabled\]** プロパティを **\[True\]** に設定します。  
  
4.  保存ボタンをダブルクリックして、イベント ハンドラーを作成し、コード エディターに切り替えます。  
  
5.  保存ボタンのイベント ハンドラーに次のコードを追加します。  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## 更新 \(Insert、Update、および Delete\) の実行に対する既定の動作のオーバーライド  
  
#### 既定の更新動作をオーバーライドするには  
  
1.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で LINQ to SQL ファイルを開きます \(**ソリューション エクスプローラー**で **Northwind.dbml** ファイルをダブルクリックします\)。  
  
2.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind データベースの **\[ストアド プロシージャ\]** ノードを展開し、**InsertCustomers**、**UpdateCustomers**、および **DeleteCustomers** の各ストアド プロシージャを探します。  
  
3.  3 つのストアド プロシージャをすべて [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。  
  
     各ストアド プロシージャが <xref:System.Data.Linq.DataContext> のメソッドとしてメソッド ペインに追加されます。詳細については、「[DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)」を参照してください。  
  
4.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で **\[Customer\]** エンティティ クラスを選択します。  
  
5.  **\[プロパティ\]** ウィンドウで **\[Insert\]** プロパティを選択します。  
  
6.  **\[ランタイムを使用\]** の横にある省略記号 \(\[...\]\) をクリックして、**\[動作の構成\]** ダイアログ ボックスを開きます。  
  
7.  **\[カスタマイズ\]** を選択します。  
  
8.  **\[カスタマイズ\]** ボックスの一覧の **\[InsertCustomers\]** メソッドをクリックします。  
  
9. **\[適用\]** をクリックして、選択したクラスと動作の構成を保存します。  
  
    > [!NOTE]
    >  変更を行うたびに **\[適用\]** をクリックすると、各クラスと動作の組み合わせに対して動作の構成を続行できます。**\[適用\]** をクリックする前にクラスまたは動作を変更した場合は、警告ダイアログ ボックスが表示され、ここで変更を適用できます。  
  
10. **\[動作\]** ボックスの一覧の **\[Update\]** をクリックします。  
  
11. **\[カスタマイズ\]** を選択します。  
  
12. **\[カスタマイズ\]** ボックスの一覧の **\[UpdateCustomers\]** メソッドをクリックします。  
  
     **\[メソッドの引数\]** および **\[クラスのプロパティ\]** の一覧を調べると、テーブルの一部の列には 2 つの**メソッドの引数**と 2 つの**クラスのプロパティ**があることがわかります。これにより、変更を追跡したり、同時実行違反をチェックするステートメントを作成したりすることが簡単になります。  
  
13. **Original\_CustomerID** メソッド引数を **CustomerID \(オリジナル\)** クラス プロパティにマップします。  
  
    > [!NOTE]
    >  既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。プロパティ名が変更され、テーブルとエンティティ クラス間で一致しなくなったために、O\/R デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。また、メソッド引数のマップ先として有効なクラス プロパティがない場合は、**\[クラスのプロパティ\]** の値を **\[\(なし\)\]** に設定できます。  
  
14. **\[適用\]** をクリックして、選択したクラスと動作の構成を保存します。  
  
15. **\[動作\]** ボックスの一覧の **\[Delete\]** をクリックします。  
  
16. **\[カスタマイズ\]** を選択します。  
  
17. **\[カスタマイズ\]** ボックスの一覧の **\[DeleteCustomers\]** メソッドをクリックします。  
  
18. **Original\_CustomerID** メソッド引数を **CustomerID \(オリジナル\)** クラス プロパティにマップします。  
  
19. **\[OK\]** をクリックします。  
  
> [!NOTE]
>  この特定のチュートリアルに限った問題ではありませんが、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] は、ID 列 \(自動インクリメント\)、rowguidcol 列 \(データベースが生成した GUID\)、およびタイムスタンプ列であれば、データベースによって生成された値を、挿入時および更新時に自動的に処理します。その他の列型のデータベースによって生成された値は、予想に反して null 値になります。データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を <xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync>、または <xref:System.Data.Linq.Mapping.AutoSync> のいずれかに設定する必要があります。  
  
## アプリケーションのテスト  
 アプリケーションを再実行し、データベース内の顧客レコードが **UpdateCustomers** ストアド プロシージャによって正しく更新されることを確認します。  
  
#### アプリケーションをテストするには  
  
1.  F5 キーを押します。  
  
2.  グリッド内のレコードを変更して、Update の動作をテストします。  
  
3.  新しいレコードを追加して、Insert の動作をテストします。  
  
4.  保存ボタンをクリックして、変更をデータベースに保存します。  
  
5.  フォームを閉じます。  
  
6.  F5 キーを押し、更新されたレコードと新しく挿入したレコードが永続化されていることを確認します。  
  
7.  手順 3. で作成した新しいレコードを削除して、Delete の動作をテストします。  
  
8.  保存ボタンをクリックして変更を送信し、削除されたレコードをデータベースから削除します。  
  
9. フォームを閉じます。  
  
10. F5 キーを押し、削除したレコードがデータベースから削除されていることを確認します。  
  
    > [!NOTE]
    >  アプリケーションで SQL Server Express Edition を使用している場合、データベース ファイルの **\[出力ディレクトリにコピー\]** プロパティの値によっては、手順 10. で F5 キーを押したときに変更が表示されない場合があります。詳細については、「[方法 : プロジェクトでローカル データ ファイルを管理する](../data-tools/how-to-manage-local-data-files-in-your-project.md)」を参照してください。  
  
## 次の手順  
 アプリケーションの要件に応じて、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラスの作成後にいくつかの手順を実行することが必要な場合があります。このアプリケーションで行うことができる拡張には次のものがあります。  
  
-   更新時の同時実行チェックを実装します。詳細については、「[Optimistic Concurrency: Overview](../Topic/Optimistic%20Concurrency:%20Overview.md)」を参照してください。  
  
-   LINQ クエリを追加してデータをフィルター処理します。詳細については、「[Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)」を参照してください。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to SQL Queries](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/ja-jp/3d50d68f-5f44-4915-842f-6d42fce793f1)