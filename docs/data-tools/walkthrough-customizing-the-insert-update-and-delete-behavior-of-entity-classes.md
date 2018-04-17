---
title: 'チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 38dc02e4c1cd7a0d6bead05a585b878f242209ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除

[LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)の作成と編集、ビジュアル デザイン画面を提供[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]データベース内のオブジェクトに基づくクラス (エンティティ クラス)。 使用して[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)、SQL データベースにアクセスする LINQ テクノロジを使用することができます。 詳細については、「[LINQ (Language-Integrated Query) (LINQ (統合言語クエリ))](/dotnet/csharp/linq/)」をご覧ください。  
  
既定では、更新を実行するロジックは [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムによって提供されます。 ランタイムは、テーブルのスキーマ (列定義と主キー情報) に基づいて、既定の Insert、Update、および Delete の各ステートメントを作成します。 既定の動作を使用しない場合は、更新動作を構成し、データベースのデータの操作に必要な Insert、Update、および Delete を実行する特定のストアド プロシージャを指定できます。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 また、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。 詳細については、次を参照してください。[のカスタマイズの操作によってストアド プロシージャの使用](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)です。  
  
> [!NOTE]
> このチュートリアルでは、可用性、 **InsertCustomer**、 **UpdateCustomer**、および**DeleteCustomer**のため、Northwind データベースのストアド プロシージャ。  
  
このチュートリアルでは、ストアド プロシージャを使用して、データベースにデータを保存する既定の LINQ to SQL ランタイムの動作をオーバーライドするために必要な手順を示します。  
  
このチュートリアルでは、次のタスクを実行する方法を学習します。  
  
-   新しい Windows フォーム アプリケーションを作成し、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ファイルを追加します。  
  
-   Northwind の Customers テーブルにマップされるエンティティ クラスを作成します。  
  
-   LINQ to SQL Customer クラスを参照するオブジェクト データ ソースを作成します。  
  
-   Customer クラスにバインドされる <xref:System.Windows.Forms.DataGridView> を含む Windows フォームを作成します。  
  
-   フォームの保存機能を実装します。  
  
-   <xref:System.Data.Linq.DataContext>にストアド プロシージャを追加することにより、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] のメソッドを作成します。  
  
-   ストアド プロシージャを使用して挿入、更新、および削除を実行するように Customer クラスを構成します。  
  
## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。  
  
1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。  
  
2.  次の手順に従って、Northwind サンプル データベースをインストールします。  

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.  

       クエリ エディター ウィンドウが開きます。  

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。  

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。  

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>アプリケーションの作成と LINQ to SQL クラスの追加

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスを操作してデータを Windows フォームに表示できるように、新しい Windows フォーム アプリケーションを作成し、LINQ to SQL クラス ファイルを追加します。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには、を格納している LINQ to SQL クラス
  
1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.  
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**UpdatingWithSProcsWalkthrough**を選択し**OK**です。 
  
     **UpdatingWithSProcsWalkthrough**プロジェクトが作成され、追加する**ソリューション エクスプ ローラー**です。  
  
4.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
5.  クリックして、 **LINQ to SQL クラス**テンプレートと型**Northwind.dbml**で、**名前**ボックス。  
  
6.  **[追加]** をクリックします。  
  
     プロジェクトに空の LINQ to SQL クラス ファイル (Northwind.dbml) が追加され、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]が開きます。  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Customer エンティティ クラスとオブジェクト データ ソースの作成

作成[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]からテーブルをドラッグして、データベース テーブルにマップされているクラス**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 結果は、データベース内のテーブルにマップされた LINQ to SQL エンティティ クラスになります。 作成したエンティティ クラスは、パブリック プロパティを持つ他のクラスと同様に、オブジェクト データ ソースとして使用できます。  
  
### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Customer エンティティ クラスを作成し、そのエンティティ クラスでデータ ソースを構成するには
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind サンプル データベースの SQL Server バージョン内で顧客テーブルを検索します。 
  
2.  ドラッグ、**顧客**からノード**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]画面。  
  
     名前付きエンティティ クラス**顧客**を作成します。 これには、Customers テーブルの列に対応するプロパティが含まれています。 エンティティ クラスの名前は**顧客**(いない**顧客**) Customers テーブルから 1 人の顧客を表すためです。  
  
    > [!NOTE]
    >  この名前の変更の動作は呼び出されます*複数形化*です。 オンまたはオフにすることができます、[オプション ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)です。 詳細については、次を参照してください。[する方法: 複数形化のオンとオフ (O/r デザイナー)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)です。  
  
3.  **ビルド** メニューのをクリックして**updatingwithsprocswalkthrough のビルド**プロジェクトをビルドします。  
  
4.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
5.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]**をクリックします。  
  
6.  をクリックして**オブジェクト**上、**データ ソースの種類を選択**ページし、をクリックして**[次へ]**です。  
  
7.  展開、 **UpdatingwithSProcsWalkthrough**ノード検索して選択し、**顧客**クラスです。  
  
    > [!NOTE]
    >  場合、**顧客**クラスは使用できません、ウィザードをキャンセル、プロジェクトをビルド、およびウィザードを再度実行します。  
8.  をクリックして**完了**データ ソースを作成し、追加、**顧客**エンティティ クラスを**データ ソース**ウィンドウです。  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Windows フォームに顧客データを表示するための DataGridView の作成

ドラッグしてエンティティ クラスにバインドされるコントロールを作成する[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]データ ソースからの項目、**データソース**ウィンドウから Windows フォームにします。  
  
### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>エンティティ クラスにバインドされるコントロールを追加するには
  
1.  デザイン ビューで [Form1] を開きます。  
  
2.  **データソース**ウィンドウで、ドラッグ、**顧客**ノードを Form1 にします。  
  
    > [!NOTE]
    > 表示する、**データ ソース**ウィンドウで、をクリックして**データ ソースの表示**で、**データ**メニュー。  
  
3.  コード エディターで Form1 を開きます。  
  
4.  フォームに次のコードを追加します。フォームに対してグローバルになるように、Form1 クラスの内部でありながら、どのメソッドにも属さない位置に追加します。  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  `Form_Load` イベントのイベント ハンドラーを作成し、ハンドラーに次のコードを追加します。  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>保存機能の実装

既定では、保存ボタンが有効ではなく、保存機能は実装されていません。 また、オブジェクト データ ソースに対してデータ バインド コントロールを作成しても、変更されたデータをデータベースに保存するコードは自動的には追加されません。 ここでは、保存ボタンを有効にし、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] オブジェクトの保存機能を実装する方法について説明します。  
  
### <a name="to-implement-save-functionality"></a>保存機能を実装するには
  
1.  デザイン ビューで [Form1] を開きます。  
  
2.  保存先の選択ボタンをクリックして、 **CustomerBindingNavigator** (フロッピー ディスクのアイコンのボタン)。  
  
3.  **プロパティ**ウィンドウで、設定、**有効**プロパティを**True**です。  
  
4.  保存ボタンをダブルクリックして、イベント ハンドラーを作成し、コード エディターに切り替えます。  
  
5.  保存ボタンのイベント ハンドラーに次のコードを追加します。  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>更新 (Insert、Update、および Delete) の実行に対する既定の動作のオーバーライド
  
### <a name="to-override-the-default-update-behavior"></a>既定の更新動作をオーバーライドするには
  
1.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で LINQ to SQL ファイルを開きます  (ダブルクリックして、 **Northwind.dbml**ファイル**ソリューション エクスプ ローラー**)。  
  
2.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースを展開して**ストアド プロシージャ**ノードを検索し、 **InsertCustomers**、 **UpdateCustomers**、および**DeleteCustomers**ストアド プロシージャです。  
  
3.  3 つのストアド プロシージャをすべて [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。  
  
     各ストアド プロシージャが <xref:System.Data.Linq.DataContext> のメソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。  
  
4.  選択、**顧客**のエンティティ クラスに、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。  
  
5.  **プロパティ**ウィンドウで、**挿入**プロパティです。  
  
6.  横にある省略記号 (...) をクリックして**ランタイムを使用**を開くには、**動作の構成** ダイアログ ボックス。  
  
7.  選択**カスタマイズ**です。  
  
8.  選択、 **InsertCustomers**メソッドで、**カスタマイズ** ボックスの一覧です。  
  
9. をクリックして**適用**選択したクラスと動作の構成を保存します。  
  
    > [!NOTE]
    >  をクリックする限り、各クラスと動作の組み合わせに対して動作の構成を続行できます**適用**各変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**変更を適用する機会が表示され、警告ダイアログ ボックス。  
  
10. 選択**更新**で、**動作** ボックスの一覧です。  
  
11. 選択**カスタマイズ**です。  
  
12. 選択、 **UpdateCustomers**メソッドで、**カスタマイズ** ボックスの一覧です。  
  
     一覧を調べる**メソッド引数**と**クラス プロパティ**が含まれている 2 つと**メソッドの引数**と 2 つ**クラス プロパティ**一部の列、テーブルにします。 これにより、変更を追跡したり、同時実行違反をチェックするステートメントを作成したりすることが簡単になります。  
  
13. マップ、 **Original_CustomerID**メソッド引数を**CustomerID (オリジナル)**クラスのプロパティです。  
  
    > [!NOTE]
    >  既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 プロパティ名が変更され、テーブルとエンティティ クラス間で一致しなくなったために、O/R デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。 さらに、メソッドの引数があるない有効なクラス プロパティにマップする場合を設定できます、**クラス プロパティ**値**(なし)**です。  
  
14. をクリックして**適用**選択したクラスと動作の構成を保存します。  
  
15. 選択**削除**で、**動作** ボックスの一覧です。  
  
16. 選択**カスタマイズ**です。  
  
17. 選択、 **DeleteCustomers**メソッドで、**カスタマイズ** ボックスの一覧です。  
  
18. マップ、 **Original_CustomerID**メソッド引数を**CustomerID (オリジナル)**クラスのプロパティです。  
  
19. **[OK]**をクリックします。  
  
> [!NOTE]
> この特定のチュートリアルに限った問題ではありませんが、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] は、ID 列 (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列であれば、データベースによって生成された値を、挿入時および更新時に自動的に処理します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を <xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync>、または <xref:System.Data.Linq.Mapping.AutoSync> のいずれかに設定する必要があります。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト

確認するには、もう一度アプリケーションを実行、 **UpdateCustomers**ストアド プロシージャが正しく、データベース内の顧客レコードを更新します。

### <a name="to-test-the-application"></a>アプリケーションをテストするには

1.  F5 キーを押します。  
  
2.  グリッド内のレコードを変更して、Update の動作をテストします。  
  
3.  新しいレコードを追加して、Insert の動作をテストします。  
  
4.  保存ボタンをクリックして変更をデータベースに保存します。  
  
5.  フォームを閉じます   
  
6.  F5 キーを押し、更新されたレコードと新しく挿入したレコードが永続化されていることを確認します。  
  
7.  手順 3. で作成した新しいレコードを削除して、Delete の動作をテストします。  
  
8.  保存ボタンをクリックして変更を送信し、削除されたレコードをデータベースから削除します。  
  
9. フォームを閉じます   
  
10. F5 キーを押し、削除したレコードがデータベースから削除されていることを確認します。  
  
    > [!NOTE]
    > アプリケーションがの値に応じて SQL Server Express Edition を使用するかどうか、**出力ディレクトリにコピー**データベース ファイルのプロパティを変更されない可能性があります手順 10. で f5 キーを押す。

## <a name="next-steps"></a>次の手順

アプリケーションの要件に応じて、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラスの作成後にいくつかの手順を実行することが必要な場合があります。 このアプリケーションで行うことができる拡張には次のものがあります。

- 更新時の同時実行チェックを実装します。 詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)です。

- LINQ クエリを追加してデータをフィルター処理します。 詳細については、次を参照してください。 [LINQ クエリ (c#) の概要](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)です。

## <a name="see-also"></a>関連項目

[Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
[DataContext メソッド](../data-tools/datacontext-methods-o-r-designer.md)  
[方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[LINQ to SQL クエリ](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)