---
title: 単純なデータ バインディングをサポートするユーザー コントロールを作成する
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 673e510536ab866f3be90da630d3cfa261bb98c6
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305404"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>単純なデータ バインディングをサポートする Windows フォーム ユーザー コントロールの作成

Windows アプリケーションのフォームにデータを表示する場合は、**[ツールボックス]** から既存のコントロールを選択するか、またはアプリケーションが標準コントロールでは提供できない機能を必要とする場合は、カスタム コントロールを記述できます。 このチュートリアルでは、<xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールには、データにバインドできるプロパティを 1 つ含めることができます。 このようなコントロールは、<xref:System.Windows.Forms.TextBox> や <xref:System.Windows.Forms.CheckBox> に似ています。

コントロールの作成の詳細については、次を参照してください。[デザイン時に Windows フォーム コントロールの開発](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)します。

データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性のいずれかを実装する必要があります。

|データ バインディング属性の使用方法|
| - |
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)です。|
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|

このチュートリアルでは、テーブルの単一の列のデータを表示する簡単なコントロールを作成します。 この例では、Northwind サンプル データベースの `Phone` テーブルの `Customers` 列を使用します。 単純なユーザー コントロールを使用して、標準の電話番号形式で顧客の電話番号が表示されます、<xref:System.Windows.Forms.MaskedTextBox>電話番号にマスクを設定するとします。

このチュートリアルでは、次の作業を行う方法について説明します。

-   新しい **Windows フォーム アプリケーション**を作成します。

-   新しい**ユーザー コントロール**をプロジェクトに追加します。

-   ユーザー コントロールをビジュアルに設計します。

-   `DefaultBindingProperty` 属性を実装します。

-   使用してデータセットを作成、**データ ソースの構成**ウィザード。

-   **[データ ソース]** ウィンドウで **[Phone]** 列が新しいコントロールを使用するように設定します。

-   フォームを作成して、新しいコントロールにデータを表示します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**ワークロードで、 **Visual Studio インストーラー**)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成する

作成するには、まず、 **Windows フォーム アプリケーション**:

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**SimpleControlWalkthrough**を選び、 **OK**。

     **SimpleControlWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。

## <a name="add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加する

このチュートリアルから単純なデータ バインド可能なコントロールを作成、**ユーザー コントロール**します。 追加、**ユーザー コントロール**項目を**SimpleControlWalkthrough**プロジェクト。

1.  **[プロジェクト]** メニューの **[ユーザー コントロールの追加]** を選択します。

2.  [ファイル名] 領域に「**PhoneNumberBox**」と入力し、**[追加]** をクリックします。

     **PhoneNumberBox** コントロールが **ソリューション エクスプローラー**に追加され、デザイナーが開きます。

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox コントロールをデザインします。

このチュートリアルでは、既存<xref:System.Windows.Forms.MaskedTextBox>を作成する、 **PhoneNumberBox**コントロール。

1.  **ツールボックス**からユーザー コントロールのデザイン サーフェイスに <xref:System.Windows.Forms.MaskedTextBox> をドラッグします。

2.  ドラッグした <xref:System.Windows.Forms.MaskedTextBox> のスマート タグを選択し、**[マスクの設定]** を選択します。

3.  **[定型入力]** ダイアログ ボックスで **[電話番号]** を選択し、**[OK]** をクリックしてマスクを設定します。

## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。

データ バインディングをサポートする簡単なコントロールに対しては <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装します。

1.  スイッチ、 **PhoneNumberBox**コントロールをコード ビューにします。 (**[表示]** メニューの **[コード]** を選択します。)

2.  コードに置き換えます、 **PhoneNumberBox**次。

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。

この手順では、**データ ソース構成**ウィザードを使用して、Northwind サンプル データベースの `Customers` テーブルに基づいてデータ ソースを作成します。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースのセットアップについては、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)します。

1.  開くには、**データ ソース**ウィンドウで、**データ**] メニューのをクリックして **[データ ソースの**します。

2.  **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成**ウィザードを起動します。

3.  **[データソースの種類を選択]** ページで、**[データベース]** を選択し、**[次へ]** をクリックします。

4.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを表示します。

5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**[次へ]** をクリックします。

6.  **[アプリケーション構成ファイルに接続文字列を保存]** ページで、**[次へ]** をクリックします。

7.  **[データベース オブジェクトの選択]** ページで、**[テーブル]** ノードを展開します。

8.  `Customers` テーブルを選択し、**[完了]** をクリックします。

     プロジェクトに **NorthwindDataSet** が追加され、**[データ ソース]** ウィンドウに `Customers` テーブルが表示されます。

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>PhoneNumberBox コントロールを使用して、phone 列を設定します。

**[データ ソース]** ウィンドウでは、フォームにコントロールをドラッグする前に作成するコントロールを設定できます。

1.  デザイナーで **Form1** を開きます。

2.  **[データ ソース]** ウィンドウの **[Customers]** ノードを展開します。

3.  **[Customers]** ノードのドロップダウン矢印をクリックし、コントロール リストの **[Details]** を選択します。

4.  **[Phone]** 列のドロップダウン矢印をクリックし、**[Customize]** をクリックします。

5.  **[データ UI カスタマイズ オプション]** ダイアログ ボックスの **[関連付けられたコントロール]** の一覧の **[PhoneNumberBox]** を選択します。

6.  **[Phone]** 列のドロップダウン矢印をクリックし、**[PhoneNumberBox]** をクリックします。

## <a name="add-controls-to-the-form"></a>コントロールをフォームに追加します。

**[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。

フォーム上のデータ バインド コントロールを作成するには、メインをドラッグします**顧客**ノードから、**データ ソース**ウィンドウから、フォームにいることを確認し、 **PhoneNumberBox**コントロールが。データを表示するために使用、 **Phone**列。

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>アプリケーションの実行

**F5** キーを押してアプリケーションを実行します。

## <a name="next-steps"></a>次の手順

アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。 次の手順として、一般的には、次のようなことを実行します。

-   他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。

-   より複雑なデータ バインディングのシナリオをサポートするコントロールを作成します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)と[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)