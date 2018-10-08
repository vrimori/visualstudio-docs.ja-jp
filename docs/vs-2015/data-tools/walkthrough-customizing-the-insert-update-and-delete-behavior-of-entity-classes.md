---
title: 'チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作の削除 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b4bc04af81d3617646f5c7311919ad9ef36a28d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535984"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: 更新、およびエンティティ クラスの動作を削除、挿入をカスタマイズするには、](https://docs.microsoft.com/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)します。  
  
  
[LINQ to SQL ツール Visual Studio で](../data-tools/linq-to-sql-tools-in-visual-studio2.md)の作成と編集のビジュアル デ ザイン サーフェイスを提供します。[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]データベース内のオブジェクトに基づくクラス (エンティティ クラス)。 使用して[LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)、SQL データベースにアクセスする LINQ テクノロジを使用することができます。 詳細については、「[LINQ (Language-Integrated Query) (LINQ (統合言語クエリ))](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)」をご覧ください。  
  
 既定では、更新を実行するロジックは [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ランタイムによって提供されます。 ランタイムは、テーブルのスキーマ (列定義と主キー情報) に基づいて、既定の Insert、Update、および Delete の各ステートメントを作成します。 既定の動作を使用しない場合は、更新動作を構成し、データベースのデータの操作に必要な Insert、Update、および Delete を実行する特定のストアド プロシージャを指定できます。 この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。 また、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。 詳細については、次を参照してください。[カスタマイズ操作ストアド プロシージャによる](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a)します。  
  
> [!NOTE]
>  このチュートリアルでは、可用性、 **InsertCustomer**、 **UpdateCustomer**、および**DeleteCustomer**のため、Northwind データベースのストアド プロシージャ。 これらのストアド プロシージャを作成する方法の詳細については、次を参照してください。[チュートリアル: Northwind の Customers テーブル用の更新ストアド プロシージャの作成](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)です。  
  
 このチュートリアルでは、ストアド プロシージャを使用して、データベースにデータを保存する既定の LINQ to SQL ランタイムの動作をオーバーライドするために必要な手順を示します。  
  
 このチュートリアルでは、次のタスクを実行する方法を学習します。  
  
-   新しい Windows フォーム アプリケーションを作成し、[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ファイルを追加します。  
  
-   Northwind の Customers テーブルにマップされるエンティティ クラスを作成します。  
  
-   LINQ to SQL Customer クラスを参照するオブジェクト データ ソースを作成します。  
  
-   Customer クラスにバインドされる <xref:System.Windows.Forms.DataGridView> を含む Windows フォームを作成します。  
  
-   フォームの保存機能を実装します。  
  
-   <xref:System.Data.Linq.DataContext>にストアド プロシージャを追加することにより、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] のメソッドを作成します。  
  
-   ストアド プロシージャを使用して挿入、更新、および削除を実行するように Customer クラスを構成します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するための要件は次のとおりです。  
  
-   Northwind サンプル データベースの SQL Server バージョンにアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
-   **InsertCustomer**、 **UpdateCustomer**、および**DeleteCustomer**のため、Northwind データベースのストアド プロシージャ。 詳細については、次を参照してください。[チュートリアル: Northwind の Customers テーブル用の更新ストアド プロシージャの作成](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)です。  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>アプリケーションの作成と LINQ to SQL クラスの追加  
 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] クラスを操作してデータを Windows フォームに表示できるように、新しい Windows フォーム アプリケーションを作成し、LINQ to SQL クラス ファイルを追加します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>LINQ to SQL クラスを含む新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プロジェクトに名前を**UpdatingwithSProcsWalkthrough**します。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]は [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] プロジェクトと C# プロジェクトでサポートされています。 したがって、新しいプロジェクトはこれらの言語のどちらかで作成してください。  
  
3.  をクリックして、 **Windows フォーム アプリケーション**テンプレートとクリック**OK**。 詳細については、次を参照してください。[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     UpdatingwithSProcsWalkthrough プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。  
  
4.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
5.  をクリックして、 **LINQ to SQL クラス**テンプレートと種類**Northwind.dbml**で、**名前**ボックス。  
  
6.  **[追加]** をクリックします。  
  
     プロジェクトに空の LINQ to SQL クラス ファイル (Northwind.dbml) が追加され、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]が開きます。  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Customer エンティティ クラスとオブジェクト データ ソースの作成  
 作成[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]からテーブルをドラッグして、データベース テーブルにマップされているクラス**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。 結果は、データベース内のテーブルにマップされた LINQ to SQL エンティティ クラスになります。 作成したエンティティ クラスは、パブリック プロパティを持つ他のクラスと同様に、オブジェクト データ ソースとして使用できます。  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Customer エンティティ クラスを作成し、そのエンティティ クラスでデータ ソースを構成するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind サンプル データベースの SQL Server のバージョンの Customer テーブルを探します。 詳細については、次を参照してください。[方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)します。  
  
2.  ドラッグ、**顧客**ノードから**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]画面。  
  
     という名前のエンティティ クラス**顧客**が作成されます。 これには、Customers テーブルの列に対応するプロパティが含まれています。 エンティティ クラスの名前は**顧客**(いない**顧客**) Customers テーブルから単一の顧客を表すため。  
  
    > [!NOTE]
    >  この名前の変更動作*複数形化*します。 オンまたはオフにすることができます、[オプション ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)します。 詳細については、次を参照してください。[方法: 複数形化のオンとオフにする (O/r デザイナー)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)します。  
  
3.  **ビルド** メニューのをクリックして**updatingwithsprocswalkthrough のビルド**プロジェクトをビルドします。  
  
4.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
5.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。  
  
6.  をクリックして**オブジェクト**で、**データ ソースの種類を選択**ページをクリックして**次**。  
  
7.  展開、 **UpdatingwithSProcsWalkthrough**ノードを検索して、選択、**顧客**クラス。  
  
    > [!NOTE]
    >  場合、**顧客**クラスは使用できません、ウィザードをキャンセル、プロジェクトをビルド、およびウィザードを再度実行します。  
  
8.  をクリックして**完了**、データ ソースを作成し、追加、**顧客**エンティティ クラスを**データ ソース**ウィンドウ。  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Windows フォームに顧客データを表示するための DataGridView の作成  
 コントロールをドラッグして、エンティティ クラスにバインドされている作成[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]データ ソースからの項目、**データ ソース**ウィンドウから Windows フォームにします。  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>エンティティ クラスにバインドされるコントロールを追加するには  
  
1.  デザイン ビューで [Form1] を開きます。  
  
2.  **データソース**ウィンドウで、ドラッグ、**顧客**ノードを Form1 にします。  
  
    > [!NOTE]
    >  表示する、**データ ソース**ウィンドウで、をクリックして**データ ソースの表示**で、**データ**メニュー。  
  
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
 既定では、保存ボタンが有効ではなく、保存機能は実装されていません。 また、オブジェクト データ ソースに対してデータ バインド コントロールを作成しても、変更されたデータをデータベースに保存するコードは自動的には追加されません。 ここでは、保存ボタンを有効にし、[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] オブジェクトの保存機能を実装する方法について説明します。  
  
#### <a name="to-implement-save-functionality"></a>保存機能を実装するには  
  
1.  デザイン ビューで [Form1] を開きます。  
  
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
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>更新 (Insert、Update、および Delete) の実行に対する既定の動作のオーバーライド  
  
#### <a name="to-override-the-default-update-behavior"></a>既定の更新動作をオーバーライドするには  
  
1.  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]で LINQ to SQL ファイルを開きます  (ダブルクリックして、 **Northwind.dbml**ファイル**ソリューション エクスプ ローラー**)。  
  
2.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースを展開**Stored Procedures**ノードを検索し、 **InsertCustomers**、 **UpdateCustomers**、および**DeleteCustomers**ストアド プロシージャ。  
  
3.  3 つのストアド プロシージャをすべて [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]にドラッグします。  
  
     各ストアド プロシージャが <xref:System.Data.Linq.DataContext> のメソッドとしてメソッド ペインに追加されます。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。  
  
4.  選択、**顧客**内のエンティティ クラス、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。  
  
5.  **プロパティ**ウィンドウで、**挿入**プロパティ。  
  
6.  横にある省略記号 (...) をクリックします。**ランタイムを使用**を開く、**動作の構成** ダイアログ ボックス。  
  
7.  選択**カスタマイズ**します。  
  
8.  選択、 **InsertCustomers**メソッドで、**カスタマイズ**一覧。  
  
9. クリックして**適用**選択したクラスと動作の構成を保存します。  
  
    > [!NOTE]
    >  クリックすると、各クラスと動作の組み合わせの動作を構成を続行できます**適用**それぞれの変更を行った後。 クリックする前に、クラスまたは動作を変更するかどうかは**適用**、警告ダイアログ ボックスを提供するすべての変更を適用する機会が表示されます。  
  
10. 選択**Update**で、**動作**一覧。  
  
11. 選択**カスタマイズ**します。  
  
12. 選択、 **UpdateCustomers**メソッドで、**カスタマイズ**一覧。  
  
     一覧を調べて**メソッドの引数**と**クラスのプロパティ**2 に注意してくださいと**メソッドの引数**と 2 つ**クラス プロパティ**一部の列、テーブルにします。 これにより、変更を追跡したり、コンカレンシー違反をチェックするステートメントを作成したりすることが簡単になります。  
  
13. マップ、 **Original_CustomerID**メソッド引数に、 **CustomerID (オリジナル)** クラスのプロパティ。  
  
    > [!NOTE]
    >  既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。 プロパティ名が変更され、テーブルとエンティティ クラス間で一致しなくなったために、O/R デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。 さらに、メソッドの引数は有効なクラス プロパティにマップを持っていない場合は設定、**クラス プロパティ**値を **(なし)** します。  
  
14. クリックして**適用**選択したクラスと動作の構成を保存します。  
  
15. 選択**削除**で、**動作**一覧。  
  
16. 選択**カスタマイズ**します。  
  
17. 選択、 **DeleteCustomers**メソッドで、**カスタマイズ**一覧。  
  
18. マップ、 **Original_CustomerID**メソッド引数に、 **CustomerID (オリジナル)** クラスのプロパティ。  
  
19. **[OK]** をクリックします。  
  
> [!NOTE]
>  この特定のチュートリアルに限った問題ではありませんが、[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] は、ID 列 (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列であれば、データベースによって生成された値を、挿入時および更新時に自動的に処理します。 その他の列型のデータベースが生成した値は、予想に反して null 値になります。 データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を <xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync>、または <xref:System.Data.Linq.Mapping.AutoSync> のいずれかに設定する必要があります。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 いることを確認するには、もう一度アプリケーションの実行、 **UpdateCustomers**ストアド プロシージャが正しく、データベース内の顧客レコードを更新します。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
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
    >  アプリケーションがの値に応じて SQL Server Express Edition を使用するかどうか、**出力ディレクトリにコピー**データベース ファイルのプロパティは、手順 10. で f5 キーを押すとき、変更が表示されません。 詳細については、次を参照してください。[方法: プロジェクトでのローカル データ ファイルの管理](../data-tools/how-to-manage-local-data-files-in-your-project.md)します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] エンティティ クラスの作成後にいくつかの手順を実行することが必要な場合があります。 このアプリケーションで行うことができる拡張には次のものがあります。  
  
-   更新時のコンカレンシー チェックを実装します。 詳しくは、次を参照してください。[オプティミスティック同時実行制御: 概要](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694)します。  
  
-   LINQ クエリを追加してデータをフィルター処理します。 詳しくは、次を参照してください。 [LINQ クエリ (c#) の概要](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [LINQ to SQL クエリ](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)   
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Visual Studio 2012 でのデータ アプリケーションの開発の新 PAVE します。](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)

