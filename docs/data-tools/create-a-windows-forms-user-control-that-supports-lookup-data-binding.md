---
title: データ バインディング - Windows フォーム コントロールのルックアップ テーブルの使用 |Microsoft Docs
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
ms.openlocfilehash: 07c9cf40952eabcafe9d1587d3e2ae4aa02de3a0
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305083"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成する

フォームにデータを表示する場合は、**ツールボックス**から既存のコントロールを選択するか、またはアプリケーションが標準コントロールでは提供できない機能を必要とする場合は、カスタム コントロールを記述できます。 このチュートリアルでは、<xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装するコントロールには、データにバインドできるプロパティを 3 つ含めることができます。 このようなコントロールは、<xref:System.Windows.Forms.ComboBox> に似ています。

コントロールの作成の詳細については、次を参照してください。 [Windows フォームの開発は、デザイン時にコントロール](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)します。

データ バインディングのシナリオで使用するためのコントロールを作成するときは、次のいずれかのデータ バインディング属性を実装する必要があります。

|データ バインディング属性の使用方法|
| - |
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 詳細については、次を参照してください。[単純データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)です。|
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)です。|
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|

このチュートリアルでは、2 つのテーブルのデータにバインドする検索コントロールを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。 ルックアップ コントロールにバインドする、`CustomerID`フィールドを`Orders`テーブル。 この値を使用して検索、`CompanyName`から、`Customers`テーブル。

このチュートリアルで学習する方法。

-   新しい **Windows フォーム アプリケーション**を作成します。

-   新しい**ユーザー コントロール**をプロジェクトに追加します。

-   ユーザー コントロールをビジュアルに設計します。

-   `LookupBindingProperty` 属性を実装します。

-   使用してデータセットを作成、**データ ソースの構成**ウィザード。

-   **[データ ソース]** ウィンドウで **Orders** テーブルの **[CustomerID]** 列が新しいコントロールを使用するように設定します。

-   フォームを作成して、新しいコントロールにデータを表示します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-app-project"></a>Windows フォーム アプリ プロジェクトを作成します。

作成するには、まず、 **Windows フォーム アプリケーション**プロジェクト。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**LookupControlWalkthrough**を選び、 **OK**。

     **LookupControlWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。

## <a name="add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加する

このチュートリアルでは**ユーザー コントロール**から検索コントロールを作成するので、**ユーザー コントロール**の項目を **LookupControlWalkthrough** プロジェクトに追加します。

1.  **[プロジェクト]** メニューの **[ユーザー コントロールの追加]** をクリックします。

2.  型`LookupBox`で、**名前**領域、およびクリック**追加**します。

     **LookupBox** コントロールが **ソリューション エクスプローラー**に追加され、デザイナーが開きます。

## <a name="design-the-lookupbox-control"></a>LookupBox コントロールをデザインします。

LookupBox コントロールをデザインするには、ドラッグ、<xref:System.Windows.Forms.ComboBox>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。

## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。

データ バインディングをサポートする検索コントロールには、<xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装できます。

1.  **LookupBox** コントロールをコード ビューに切り替えます。 (**[表示]** メニューの **[コード]** を選択します。)

2.  `LookupBox` のコードを次のコードで置き換えます。

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。

この手順では、**データ ソース構成**ウィザードを使用して、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルに基づいてデータ ソースを作成します。

1.  開くには、**データ ソース**ウィンドウで、**データ**] メニューのをクリックして **[データ ソースの**します。

2.  **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成**ウィザードを起動します。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを表示します。

5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**[次へ]** をクリックします。

6.  **[アプリケーション構成ファイルに接続文字列を保存]** ページで、**[次へ]** をクリックします。

7.  **[データベース オブジェクトの選択]** ページで、**[テーブル]** ノードを展開します。

8.  `Customers` テーブルと `Orders` テーブルを選択し、**[完了]** をクリックします。

     プロジェクトに **NorthwindDataSet** が追加され、**[データ ソース]** ウィンドウに `Customers` テーブルと `Orders` テーブルが表示されます。

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>LookupBox コントロールを使用して、Orders テーブルの CustomerID 列を設定します。

**[データ ソース]** ウィンドウでは、フォームにコントロールをドラッグする前に作成するコントロールを設定できます。

1.  デザイナーで **Form1** を開きます。

2.  **[データ ソース]** ウィンドウの **[Customers]** ノードを展開します。

3.  **[Fax]** 列の下の **[Customers]** 列にある **[Orders]** ノードを展開します。

4.  **[Orders]** ノードのドロップダウン矢印をクリックし、コントロール一覧の **[Details]** を選択します。

5.  **[Orders]** ノードの **[CustomerID]** 列のドロップダウン矢印をクリックし、**[Customize]** をクリックします。

6.  **[データ UI カスタマイズ オプション]** ダイアログ ボックスの **[関連付けられたコントロール]** の一覧の **[LookupBox]** を選択します。

7.  **[OK]** をクリックします。

8.  **[CustomerID]** 列のドロップダウン矢印をクリックし、**[LookupBox]** をクリックします。

## <a name="add-controls-to-the-form"></a>コントロールをフォームに追加します。

**[データ ソース]** ウィンドウから **Form1** に項目をドラッグして、データ バインディング コントロールを作成します。

Windows フォーム上のデータ バインド コントロールを作成するには、ドラッグ、**注文**ノードから、**データ ソース**ウィンドウから Windows フォームにことを確認します、 **LookupBox**コントロールは、データを表示するために使用、`CustomerID`列。

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Customers テーブルから CompanyName を検索するコントロールをバインドします。

検索バインドを設定するには、メインを選択します**顧客**内のノード、**データソース**ウィンドウで、とに、コンボ ボックスにドラッグ、 **CustomerIDLookupBox** で **。Form1**します。

これによって、`Orders` テーブルの `CustomerID` 値を維持しながら、`Customers` テーブルの `CompanyName` を表示するためのデータ バインディングがセットアップされます。

## <a name="run-the-application"></a>アプリケーションの実行

-   **F5** キーを押してアプリケーションを実行します。

-   レコード間を移動し、`LookupBox` コントロールに `CompanyName` が表示されることを確認します。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)