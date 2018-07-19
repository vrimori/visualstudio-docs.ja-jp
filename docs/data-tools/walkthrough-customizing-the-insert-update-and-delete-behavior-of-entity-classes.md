---
title: 'チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fb01ef51c0a44047e2caf2f23634ebe741cd2dcb
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174979"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>チュートリアル: 挿入、更新、およびエンティティ クラスの削除の動作をカスタマイズします。

[Visual Studio での LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)作成および to SQL クラス (エンティティ クラス)、データベース内のオブジェクトに基づく LINQ を編集するため、ビジュアル デ ザイン サーフェイスを提供します。 使用して[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)、SQL データベースにアクセスする LINQ テクノロジを使用することができます。 詳細については、次を参照してください。 [LINQ (Language-integrated query)](/dotnet/csharp/linq/)します。

既定では、更新プログラムを実行するロジックは、LINQ to SQL ランタイムによって提供されます。 ランタイムは、既定値を作成します。 `Insert`、 `Update`、および`Delete`(列定義と主キー情報) のテーブルのスキーマに基づいてステートメント。 既定の動作を使用しない場合は、更新動作を構成し、必要な挿入、更新、およびデータベースにデータを操作するために必要な削除を実行するための特定のストアド プロシージャを指定します。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 また、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。 詳細については、次を参照してください。[ストアド プロシージャを使用して、操作のカスタマイズ](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)します。

> [!NOTE]
> このチュートリアルでは、可用性、 **InsertCustomer**、 **UpdateCustomer**、および**DeleteCustomer**のため、Northwind データベースのストアド プロシージャ。

このチュートリアルでは、ストアド プロシージャを使用して、データベースにデータを保存する既定の LINQ to SQL ランタイムの動作をオーバーライドするために必要な手順を示します。

このチュートリアルでは、次のタスクを実行する方法について説明します。

-   新しい Windows フォーム アプリケーションを作成し、LINQ to SQL ファイルを追加します。

-   Northwind にマップされるエンティティ クラスを作成`Customers`テーブル。

-   LINQ to SQL を参照するオブジェクト データ ソース作成`Customer`クラス。

-   含む Windows フォームを作成、<xref:System.Windows.Forms.DataGridView>にバインドされている、`Customer`クラス。

-   フォームの保存機能を実装します。

-   作成<xref:System.Data.Linq.DataContext>ストアド プロシージャを追加することで、メソッド、 **O/R デザイナー**します。

-   構成、`Customer`ストアド プロシージャを使用して実行するクラスが挿入、更新、および削除します。

## <a name="prerequisites"></a>前提条件

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (**SQL Server オブジェクト エクスプ ローラー**インストールの一部として、**データ ストレージと処理**ワークロードで、 **Visual Studio インストーラー**)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>アプリケーションを作成して、LINQ to SQL クラスの追加

LINQ to SQL クラスの操作、Windows フォームでデータを表示しているため、新しい Windows フォーム アプリケーションを作成し、LINQ to SQL クラス ファイル追加します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>新しい Windows フォーム アプリケーション プロジェクトは、LINQ to SQL クラスを作成するには

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**UpdatingWithSProcsWalkthrough**を選び、 **OK**。

     **UpdatingWithSProcsWalkthrough**プロジェクトを作成するとに追加**ソリューション エクスプ ローラー**します。

4.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

5.  をクリックして、 **LINQ to SQL クラス**テンプレートと種類**Northwind.dbml**で、**名前**ボックス。

6.  **[追加]** をクリックします。

     空の LINQ to SQL クラス ファイル (**Northwind.dbml**)、プロジェクトに追加し、 **O/R デザイナー**が開きます。

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Customer エンティティ クラスとオブジェクトのデータ ソースを作成します。

LINQ to SQL クラスからテーブルをドラッグして、データベース テーブルにマップされている作成**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**します。 結果は、データベース内のテーブルにマップされた LINQ to SQL エンティティ クラスになります。 作成したエンティティ クラスは、パブリック プロパティを持つ他のクラスと同様に、オブジェクト データ ソースとして使用できます。

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Customer エンティティ クラスを作成し、そのエンティティ クラスでデータ ソースを構成するには

1.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、検索、**顧客**Northwind サンプル データベースの SQL Server のバージョンのテーブル。

2.  ドラッグ、**顧客**ノードから**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、**O/R デザイナー*画面。

     という名前のエンティティ クラス**顧客**が作成されます。 これには、Customers テーブルの列に対応するプロパティが含まれています。 エンティティ クラスの名前は**顧客**(いない**顧客**) Customers テーブルから単一の顧客を表すため。

    > [!NOTE]
    > この名前の変更動作*複数形化*します。 オンまたはオフにすることができます、[オプション ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)します。 詳細については、次を参照してください。[方法: 複数形化のオンとオフにする (O/r デザイナー)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)します。

3.  **ビルド** メニューのをクリックして**updatingwithsprocswalkthrough のビルド**プロジェクトをビルドします。

4.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

5.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

6.  をクリックして**オブジェクト**で、**データ ソースの種類を選択**ページをクリックして**次**。

7.  展開、 **UpdatingwithSProcsWalkthrough**ノードを検索して、選択、**顧客**クラス。

    > [!NOTE]
    > 場合、**顧客**クラスは使用できません、ウィザードをキャンセル、プロジェクトをビルド、およびウィザードを再度実行します。
8.  をクリックして**完了**、データ ソースを作成し、追加、**顧客**エンティティ クラスを**データ ソース**ウィンドウ。

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Windows フォームに顧客データを表示するための DataGridView を作成します。

LINQ から SQL データ ソース アイテムをドラッグすることにより、エンティティ クラスにバインドされているコントロールを作成、**データソース**ウィンドウから Windows フォームにします。

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>エンティティ クラスにバインドされるコントロールを追加するには

1.  開いている**Form1**デザイン ビューで。

2.  **データソース**ウィンドウで、ドラッグ、**顧客**上に**Form1**します。

    > [!NOTE]
    > 表示する、**データ ソース**ウィンドウで、をクリックして**データ ソースの表示**で、**データ**メニュー。

3.  開いている**Form1**コード エディターでします。

4.  フォームをフォームにどのメソッドに、グローバルに内では、次のコードを追加、`Form1`クラス。

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

## <a name="implement-save-functionality"></a>保存機能を実装します。

既定では、保存ボタンが有効ではなく、保存機能は実装されていません。 また、オブジェクト データ ソースに対してデータ バインド コントロールを作成しても、変更されたデータをデータベースに保存するコードは自動的には追加されません。 このセクションは、保存を有効にする方法を説明します。 ボタンをクリックし、SQL オブジェクトへの LINQ の保存機能を実装します。

### <a name="to-implement-save-functionality"></a>保存機能を実装するには

1.  開いている**Form1**デザイン ビューで。

2.  保存ボタンを**CustomerBindingNavigator** (フロッピー ディスクのアイコンのボタン)。

3.  **プロパティ**ウィンドウで、設定、**有効**プロパティを**True**します。

4.  保存ボタンをダブルクリックして、イベント ハンドラーを作成し、コード エディターに切り替えます。

5.  保存ボタンのイベント ハンドラーに次のコードを追加します。

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>(挿入、更新、および削除) の更新プログラムを実行するための既定の動作をオーバーライドします。

### <a name="to-override-the-default-update-behavior"></a>既定の更新動作をオーバーライドするには

1.  LINQ to SQL ファイルを開き、 **O/R デザイナー**します。 (ダブルクリックして、 **Northwind.dbml**ファイル**ソリューション エクスプ ローラー**)。

2.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、Northwind データベースを展開**Stored Procedures**ノードを検索し、 **InsertCustomers**、 **UpdateCustomers**、および**DeleteCustomers**ストアド プロシージャ。

3.  上に 3 つすべてのストアド プロシージャをドラッグして、 **O/R デザイナー**します。

     各ストアド プロシージャが <xref:System.Data.Linq.DataContext> のメソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

4.  選択、**顧客**内のエンティティ クラス、 **O/R デザイナー**します。

5.  **プロパティ**ウィンドウで、**挿入**プロパティ。

6.  省略記号をクリックします (**.**) 横に**ランタイムを使用**を開く、**動作の構成** ダイアログ ボックス。

7.  選択**カスタマイズ**します。

8.  選択、 **InsertCustomers**メソッドで、**カスタマイズ**一覧。

9. クリックして**適用**選択したクラスと動作の構成を保存します。

    > [!NOTE]
    > クリックすると、各クラスと動作の組み合わせの動作を構成を続行できます**適用**それぞれの変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**、警告ダイアログ ボックスを提供するすべての変更を適用する機会が表示されます。

10. 選択**Update**で、**動作**一覧。

11. 選択**カスタマイズ**します。

12. 選択、 **UpdateCustomers**メソッドで、**カスタマイズ**一覧。

     一覧を調べて**メソッドの引数**と**クラスのプロパティ**2 に注意してくださいと**メソッドの引数**と 2 つ**クラス プロパティ**一部の列、テーブルにします。 これにより、変更を追跡したり、同時実行違反をチェックするステートメントを作成したりすることが簡単になります。

13. マップ、 **Original_CustomerID**メソッド引数に、 **CustomerID (オリジナル)** クラスのプロパティ。

    > [!NOTE]
    > 既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 プロパティ名が変更され、テーブルとエンティティ クラス間で一致しなく、場合にマップする同等のクラスのプロパティを選択する必要があります、 **O/R デザイナー**正しいマッピングを判断することはできません。 さらに、メソッドの引数は有効なクラス プロパティにマップを持っていない場合は設定、**クラス プロパティ**値を **(なし)** します。

14. クリックして**適用**選択したクラスと動作の構成を保存します。

15. 選択**削除**で、**動作**一覧。

16. 選択**カスタマイズ**します。

17. 選択、 **DeleteCustomers**メソッドで、**カスタマイズ**一覧。

18. マップ、 **Original_CustomerID**メソッド引数に、 **CustomerID (オリジナル)** クラスのプロパティ。

19. **[OK]** をクリックします。

> [!NOTE]
> LINQ to SQL の挿入時に id (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID) 列とタイムスタンプ列を自動的にデータベースによって生成された値を処理する注目すべきは特定のチュートリアルではこの問題ではありませんが、更新します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースによって生成された値を返す必要があります手動で設定する<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>に`true`と<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>、次のいずれか: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)、 [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)、または[AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)します。

## <a name="test-the-application"></a>アプリケーションをテストする

いることを確認するには、もう一度アプリケーションの実行、 **UpdateCustomers**ストアド プロシージャが正しく、データベース内の顧客レコードを更新します。

1.  **F5**キーを押します。

2.  更新プログラムの動作をテストするグリッド内のレコードを変更します。

3.  Insert 動作をテストする新しいレコードを追加します。

4.  保存ボタンをクリックして変更をデータベースに保存します。

5.  フォームを閉じます 

6.  キーを押して**F5**し、更新されたレコードと新しく挿入されたレコードが保持されていることを確認します。

7.  作成した、新しいレコードの削除は手順削除の動作をテストする 3 です。

8.  保存をクリックします。 変更を送信し、データベースから削除されたレコードを削除するボタンをクリックします。

9. フォームを閉じます 

10. キーを押して**F5**し、データベースから削除されたレコードが削除されたことを確認します。

    > [!NOTE]
    > アプリケーションがの値に応じて SQL Server Express Edition を使用するかどうか、**出力ディレクトリにコピー**データベース ファイルのプロパティ、キーを押すとき、変更が表示されない**F5**手順 10 でします。

## <a name="next-steps"></a>次の手順

アプリケーションの要件に応じて、LINQ to SQL エンティティ クラスを作成した後に実行することがありますをいくつかの手順があります。 このアプリケーションで行うことができる拡張には次のものがあります。

- 更新時の同時実行チェックを実装します。 詳しくは、次を参照してください。[オプティミスティック同時実行制御: 概要](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)します。

- LINQ クエリを追加してデータをフィルター処理します。 詳しくは、次を参照してください。 [LINQ クエリ (c#) の概要](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)します。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext メソッド](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL クエリ](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)