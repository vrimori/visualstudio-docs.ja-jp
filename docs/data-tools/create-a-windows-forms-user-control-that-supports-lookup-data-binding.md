---
title: データ バインディングの Windows フォーム コントロールのルックアップ テーブルの使用 |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 560d19c8efeaa6c1cf206bcb40fa0b11347b4217
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746521"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成します。
Windows フォームでデータを表示する場合から既存のコントロールを選択できます、**ツールボックス**、またはアプリケーションには、標準のコントロールで利用できない機能が必要な場合は、カスタム コントロールを記述できます。 このチュートリアルでは、<xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装するコントロールには、データにバインドできるプロパティを 3 つ含めることができます。 このようなコントロールは、<xref:System.Windows.Forms.ComboBox> に似ています。

 コントロールの作成の詳細については、次を参照してください。[デザイン時に Windows フォーム コントロールの開発](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)です。

 データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性のいずれかを実装する必要があります。

|データ バインディング属性の使用方法|
|-----------------------------------|
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 詳細については、次を参照してください。[単純データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成する](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)です。|
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成する](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)です。|
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|

 このチュートリアルでは、2 つのテーブルのデータにバインドする検索コントロールを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。 この検索コントロールは `CustomerID` テーブルの `Orders` フィールドにバインドされます。 コントロールは、この値を使用して `CompanyName` テーブルの `Customers` を検索します。

 このチュートリアルでは、次の作業を行う方法について説明します。

-   新しい**Windows フォーム アプリケーション**です。

-   新しい**ユーザー コントロール**をプロジェクトにします。

-   ユーザー コントロールをビジュアルに設計します。

-   `LookupBindingProperty` 属性を実装します。

-   使用してデータセットを作成、**データ ソース構成**ウィザード。

-   設定、 **CustomerID**  列、 **Orders**表で、**データ ソース**ウィンドウで、新しいコントロールを使用します。

-   フォームを作成して、新しいコントロールにデータを表示します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。
 作成するには、まず、 **Windows フォーム アプリケーション**です。

#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.

2. いずれかを展開**Visual c#** または**Visual Basic**左側のペインでを選択し、 **Windows デスクトップ**です。

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**LookupControlWalkthrough**を選択し**OK**です。

     **LookupControlWalkthrough**プロジェクトが作成され、追加する**ソリューション エクスプ ローラー**です。

## <a name="add-a-user-control-to-the-project"></a>ユーザー コントロールをプロジェクトに追加します。
 このチュートリアルから検索コントロールを作成、**ユーザー コントロール**、ため、追加、**ユーザー コントロール**項目を**LookupControlWalkthrough**プロジェクト。

#### <a name="to-add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加するには

1.  **プロジェクト**メニューの **ユーザー コントロールの追加**です。

2.  型`LookupBox`で、**名前**領域およびクリック**追加**です。

     **LookupBox**コントロールが**ソリューション エクスプ ローラー**、され、デザイナーが開きます。

## <a name="design-the-lookupbox-control"></a>LookupBox コントロールをデザインします。

#### <a name="to-design-the-lookupbox-control"></a>LookupBox コントロールを設計するには

-   ドラッグ、<xref:System.Windows.Forms.ComboBox>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。

## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。
 データ バインディングをサポートする検索コントロールには、<xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装できます。

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>LookupBindingProperties 属性を実装するには

1.  スイッチ、 **LookupBox**コントロールをコード ビューにします。 (上、**ビュー** ] メニューの [選択**コード**)。

2.  `LookupBox` のコードを次のコードで置き換えます。

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。
この手順を使用してデータ ソースを作成、**データ ソース構成**に基づいて、ウィザード、`Customers`と`Orders`Northwind サンプル データベース内のテーブルです。

#### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成**ウィザード。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **データ接続の選択**ページは、次のいずれか。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   選択**新しい接続**を起動する、**接続接続の追加/変更** ダイアログ ボックス。

5.  データベースは、パスワードを必要とする場合は、機密データを含めるし、をクリックするオプションを選択**次**です。

6.  **接続文字列をアプリケーション構成ファイルに保存** ページで、をクリックして**次**です。

7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。

8.  選択、`Customers`と`Orders`テーブル、およびクリック**完了**です。

     **NorthwindDataSet**をプロジェクトに追加され、`Customers`と`Orders`に表示されるテーブル、**データ ソース**ウィンドウです。

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>LookupBox コントロールを使用する Orders テーブルの CustomerID 列を設定します。
 内で、**データソース**ウィンドウ、フォームに項目をドラッグする前に作成されるコントロールを設定できます。

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>[CustomerID] 列を LookupBox コントロールにバインドするように設定するには

1.  開いている**Form1**デザイナーでします。

2.  展開、**顧客**内のノード、**データソース**ウィンドウです。

3.  展開、 **Orders**ノード (で 1 つ、**顧客**ノードの下、 **Fax**列)。

4.  ドロップダウン矢印をクリックして、 **Orders**  ノードを選択し、**詳細**コントロール リストからです。

5.  ドロップダウン矢印をクリックして、 **CustomerID**列 (で、 **Orders**ノード)、選択**カスタマイズ**です。

6.  選択、 **LookupBox**の一覧から**関連付けられたコントロール**で、**データ UI カスタマイズ オプション** ダイアログ ボックス。

7.  **[OK]** をクリックします。

8.  ドロップダウン矢印をクリックして、 **CustomerID**  列を選択して**LookupBox**です。

## <a name="add-controls-to-the-form"></a>フォームにコントロールを追加します。
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウ**Form1**です。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows フォームにデータ バインディング コントロールを作成するには

-   ドラッグ、 **Orders**ノードから、**データ ソース**ウィンドウから Windows フォームにいることを確認し、 **LookupBox**内のデータを表示するコントロールを使用、 `CustomerID`列です。

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Customers テーブルから CompanyName を検索するコントロールをバインドします。

#### <a name="to-setup-the-lookup-bindings"></a>検索バインドをセットアップするには

-   メインの選択**顧客**内のノード、**データソース**ウィンドウとに、コンボ ボックスにドラッグ、 **CustomerIDLookupBox**で**Form1**.

     これを表示するデータのバインドが設定、`CompanyName`から、`Customers`を維持しながら、テーブル、`CustomerID`値から、`Orders`テーブル。

## <a name="running-the-application"></a>アプリケーションの実行

#### <a name="to-run-the-application"></a>アプリケーションを実行するには

-   F5 キーを押してアプリケーションを実行します。

-   いくつかのレコード間を移動していることを確認、`CompanyName`に表示されます、`LookupBox`コントロール。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)