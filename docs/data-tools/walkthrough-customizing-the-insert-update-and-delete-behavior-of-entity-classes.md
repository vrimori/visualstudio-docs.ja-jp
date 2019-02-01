---
title: 'チュートリアル: エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 12b09ee0e0767ad98a27387e7caf79425320598b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009753"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>チュートリアル: エンティティ クラスの挿入、更新、および削除の動作をカスタマイズする

[Visual Studio での LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)作成および to SQL クラス (エンティティ クラス)、データベース内のオブジェクトに基づく LINQ を編集するため、ビジュアル デ ザイン サーフェイスを提供します。 使用して[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)、SQL データベースにアクセスする LINQ テクノロジを使用することができます。 詳細については、[LINQ (統合言語クエリ)](/dotnet/csharp/linq/) に関するページを参照してください。

既定では、更新プログラムを実行するロジックは、LINQ to SQL ランタイムによって提供されます。 ランタイムは、既定値を作成します。 `Insert`、 `Update`、および`Delete`(列定義と主キー情報) のテーブルのスキーマに基づいてステートメント。 既定の動作を使用しない場合は、更新動作を構成し、データベースのデータの操作に必要な挿入、更新および削除を実行する特定のストアド プロシージャを指定できます。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 また、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。 詳細については、次を参照してください。[ストアド プロシージャを使用して、操作のカスタマイズ](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)します。

> [!NOTE]
> このチュートリアルでは、Northwind データベースで **InsertCustomer**、**UpdateCustomer**、および **DeleteCustomer** の各ストアド プロシージャを使用できるようにしておく必要があります。

このチュートリアルでは、ストアド プロシージャを使用して、データベースにデータを保存する既定の LINQ to SQL ランタイムの動作をオーバーライドするために必要な手順を示します。

このチュートリアルでは、次のタスクを実行する方法について説明します。

-   新しい Windows フォーム アプリケーションを作成し、LINQ to SQL ファイルを追加します。

-   Northwind にマップされるエンティティ クラスを作成`Customers`テーブル。

-   LINQ to SQL を参照するオブジェクト データ ソース作成`Customer`クラス。

-   含む Windows フォームを作成、<xref:System.Windows.Forms.DataGridView>にバインドされている、`Customer`クラス。

-   フォームの保存機能を実装します。

-   作成<xref:System.Data.Linq.DataContext>ストアド プロシージャを追加することで、メソッド、 **O/R デザイナー**します。

-   構成、`Customer`ストアド プロシージャを使用して実行するクラスが挿入、更新、および削除します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (**SQL Server オブジェクト エクスプ ローラー**インストールの一部として、**データ ストレージと処理**ワークロードで、 **Visual Studio インストーラー**)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>アプリケーションの作成と LINQ to SQL クラスの追加

LINQ to SQL クラスの操作、Windows フォームでデータを表示しているため、新しい Windows フォーム アプリケーションを作成し、LINQ to SQL クラス ファイル追加します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>新しい Windows フォーム アプリケーション プロジェクトは、LINQ to SQL クラスを作成するには

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**UpdatingWithSProcsWalkthrough**を選び、 **OK**。

     **UpdatingWithSProcsWalkthrough** プロジェクトが作成されて、**ソリューション エクスプローラー**に追加されます。

4.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

5.  **[LINQ to SQL クラス]** テンプレートをクリックし、**[名前]** ボックスに「**Northwind.dbml**」と入力します。

6.  **[追加]** をクリックします。

     空の LINQ to SQL クラス ファイル (**Northwind.dbml**)、プロジェクトに追加し、 **O/R デザイナー**が開きます。

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Customer エンティティ クラスとオブジェクトのデータ ソースを作成します。

LINQ to SQL クラスからテーブルをドラッグして、データベース テーブルにマップされている作成**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**します。 結果は、データベース内のテーブルにマップされた LINQ to SQL エンティティ クラスになります。 作成したエンティティ クラスは、パブリック プロパティを持つ他のクラスと同様に、オブジェクト データ ソースとして使用できます。

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Customer エンティティ クラスを作成し、そのエンティティ クラスでデータ ソースを構成するには

1.  **サーバー エクスプ ローラー**または**データベース エクスプ ローラー**、検索、**顧客**Northwind サンプル データベースの SQL Server のバージョンのテーブル。

2.  ドラッグ、**顧客**ノードから**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、**O/R デザイナー*画面。

     **Customer** という名前のエンティティ クラスが作成されます。 これには、Customers テーブルの列に対応するプロパティが含まれています。 このエンティティ クラスは Customers テーブルの 1 人の顧客を表すため、**Customers** ではなく **Customer** という名前が付けられます。

    > [!NOTE]
    > このような名前の変更動作を*複数形化*と呼びます。 オンまたはオフにすることができます、[オプション ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)します。 詳細については、「[方法 :複数形化をオンおよびオフにする (O/R デザイナー)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)」を参照してください。

3.  **[ビルド]** メニューの **[UpdatingwithSProcsWalkthrough のビルド]** をクリックして、プロジェクトをビルドします。

4.  開くには、**データ ソース**ウィンドウで、**データ**] メニューのをクリックして **[データ ソースの**します。

5.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

6.  **[データソースの種類を選択]** ページで、**[オブジェクト]** をクリックし、**[次へ]** をクリックします。

7.  **[UpdatingwithSProcsWalkthrough]** ノードを展開し、**[Customer]** クラスを探して選択します。

    > [!NOTE]
    > **Customer** クラスが使用可能でない場合は、ウィザードをキャンセルし、プロジェクトをビルドしてからウィザードを再実行します。
8.  **[完了]** をクリックしてデータ ソースを作成し、**Customer** エンティティ クラスを **[データ ソース]** ウィンドウに追加します。

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Windows フォームに顧客データを表示するための DataGridView を作成します。

LINQ から SQL データ ソース アイテムをドラッグすることにより、エンティティ クラスにバインドされているコントロールを作成、**データソース**ウィンドウから Windows フォームにします。

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>エンティティ クラスにバインドされるコントロールを追加するには

1.  デザイン ビューで **[Form1]** を開きます。

2.  **[データ ソース]** ウィンドウから **[Form1]** に **[Customer]** ノードをドラッグします。

    > [!NOTE]
    > **[データ ソース]** ウィンドウを表示するには、**[データ]** メニューの **[データ ソースの表示]** をクリックします。

3.  コード エディターで **[Form1]** を開きます。

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

1.  デザイン ビューで **[Form1]** を開きます。

2.  **CustomerBindingNavigator** の保存ボタン (フロッピー ディスクのアイコンのボタン) を選択します。

3.  **[プロパティ]** ウィンドウで、**[Enabled]** プロパティを **[True]** に設定します。

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

1.  LINQ to SQL ファイルを開き、 **O/R デザイナー**します。 (**ソリューション エクスプローラー**で **Northwind.dbml** ファイルをダブルクリックします。)

2.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind データベースの **[ストアド プロシージャ]** ノードを展開し、**InsertCustomers**、**UpdateCustomers**、および **DeleteCustomers** の各ストアド プロシージャを探します。

3.  上に 3 つすべてのストアド プロシージャをドラッグして、 **O/R デザイナー**します。

     各ストアド プロシージャが <xref:System.Data.Linq.DataContext> のメソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

4.  選択、**顧客**内のエンティティ クラス、 **O/R デザイナー**します。

5.  **[プロパティ]** ウィンドウで **[Insert]** プロパティを選択します。

6.  **[ランタイムを使用]** の横にある省略記号 (**[...]**) をクリックして、**[動作の構成]** ダイアログ ボックスを開きます。

7.  **[カスタマイズ]** を選択します。

8.  **[カスタマイズ]** リストの **[InsertCustomers]** メソッドを選択します。

9. **[適用]** をクリックして、選択したクラスと動作の構成を保存します。

    > [!NOTE]
    > 変更を行うたびに **[適用]** をクリックすると、各クラスと動作の組み合わせに対して動作の構成を続けることができます。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**、警告ダイアログ ボックスを提供するすべての変更を適用する機会が表示されます。

10. **[動作]** リストの **[Update]** を選択します。

11. **[カスタマイズ]** を選択します。

12. **[カスタマイズ]** リストの **[UpdateCustomers]** メソッドを選択します。

     **[メソッドの引数]** および **[クラスのプロパティ]** のリストを調べると、テーブルの一部の列には 2 つの**メソッドの引数**と 2 つの**クラスのプロパティ**があることがわかります。 これにより、変更を追跡したり、コンカレンシー違反をチェックするステートメントを作成したりすることが簡単になります。

13. **Original_CustomerID** メソッド引数を **CustomerID (オリジナル)** クラス プロパティにマップします。

    > [!NOTE]
    > 既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 プロパティ名が変更され、テーブルとエンティティ クラス間で一致しなくなったために、**O/R デザイナー**が正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。 また、メソッド引数のマップ先として有効なクラス プロパティがない場合は、**[クラスのプロパティ]** 値を **[(なし)]** に設定できます。

14. **[適用]** をクリックして、選択したクラスと動作の構成を保存します。

15. **[動作]** リストの **[Delete]** を選択します。

16. **[カスタマイズ]** を選択します。

17. **[カスタマイズ]** リストの **[DeleteCustomers]** メソッドを選択します。

18. **Original_CustomerID** メソッド引数を **CustomerID (オリジナル)** クラス プロパティにマップします。

19. **[OK]** をクリックします。

> [!NOTE]
> LINQ to SQL の挿入時に id (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID) 列とタイムスタンプ列を自動的にデータベースによって生成された値を処理する注目すべきは特定のチュートリアルではこの問題ではありませんが、更新します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を 、、または  のいずれかに設定する必要があります。[AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)、 [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)、または[AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)します。

## <a name="test-the-application"></a>アプリケーションをテストする

アプリケーションを再実行し、データベース内の顧客レコードが **UpdateCustomers** ストアド プロシージャによって正しく更新されることを確認します。

1.  **F5**キーを押します。

2.  グリッド内のレコードを変更して、更新動作をテストします。

3.  新しいレコードを追加して、挿入動作をテストします。

4.  保存ボタンをクリックして変更をデータベースに保存します。

5.  フォームを閉じます 

6.  **F5** キーを押し、更新されたレコードと新しく挿入したレコードが永続化されていることを確認します。

7.  手順 3 で作成した新しいレコードを削除して、削除動作をテストします。

8.  保存ボタンをクリックして変更を送信し、削除されたレコードをデータベースから削除します。

9. フォームを閉じます 

10. **F5** キーを押し、削除したレコードがデータベースから削除されていることを確認します。

    > [!NOTE]
    > アプリケーションで SQL Server Express Edition を使用している場合、データベース ファイルの **[出力ディレクトリにコピー]** プロパティの値によっては、手順 10 で **F5** キーを押したときに変更が表示されない場合があります。

## <a name="next-steps"></a>次の手順

アプリケーションの要件に応じて、LINQ to SQL エンティティ クラスを作成した後に実行することがありますをいくつかの手順があります。 このアプリケーションで行うことができる拡張には次のものがあります。

- 更新時のコンカレンシー チェックを実装します。 詳しくは、次を参照してください。[オプティミスティック同時実行制御: 概要](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)します。

- LINQ クエリを追加してデータをフィルター処理します。 詳しくは、次を参照してください。 [LINQ クエリ (c#) の概要](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext メソッド](../data-tools/datacontext-methods-o-r-designer.md)
- [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL クエリ](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)