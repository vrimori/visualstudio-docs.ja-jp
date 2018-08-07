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
ms.openlocfilehash: ab4ee8f468b3d6fa138984e17f3bbe843082e987
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582448"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>単純データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成します。

Windows アプリケーションでフォームにデータを表示するときにから既存のコントロールを選択することができます、**ツールボックス**、またはアプリケーションが標準のコントロールで使用できない機能に必要な場合は、カスタム コントロールを作成できます。 このチュートリアルでは、<xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールには、データにバインドできるプロパティを 1 つ含めることができます。 このようなコントロールは、<xref:System.Windows.Forms.TextBox> や <xref:System.Windows.Forms.CheckBox> に似ています。

コントロールの作成の詳細については、次を参照してください。[デザイン時に Windows フォーム コントロールの開発](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)します。

データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性のいずれかを実装する必要があります。

|データ バインディング属性の使用方法|
|-----------------------------------|
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)です。|
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|

このチュートリアルでは、テーブルの単一の列のデータを表示する簡単なコントロールを作成します。 この例では、Northwind サンプル データベースの `Phone` テーブルの `Customers` 列を使用します。 単純なユーザー コントロールを使用して、標準の電話番号形式で顧客の電話番号が表示されます、<xref:System.Windows.Forms.MaskedTextBox>電話番号にマスクを設定するとします。

このチュートリアルでは、次の作業を行う方法について説明します。

-   新規作成**Windows フォーム アプリケーション**します。

-   新しい追加**ユーザー コントロール**をプロジェクトにします。

-   ユーザー コントロールをビジュアルに設計します。

-   `DefaultBindingProperty` 属性を実装します。

-   使用してデータセットを作成、**データ ソースの構成**ウィザード。

-   設定、 **Phone**内の列、**データソース**に新しいコントロールを使用するウィンドウ。

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

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。

作成するには、まず、 **Windows フォーム アプリケーション**:

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**SimpleControlWalkthrough**を選び、 **OK**。

     **SimpleControlWalkthrough**プロジェクトを作成するとに追加**ソリューション エクスプ ローラー**します。

## <a name="add-a-user-control-to-the-project"></a>ユーザー コントロールをプロジェクトに追加します。

このチュートリアルから単純なデータ バインド可能なコントロールを作成、**ユーザー コントロール**します。 追加、**ユーザー コントロール**項目を**SimpleControlWalkthrough**プロジェクト。

1.  **プロジェクト**] メニューの [選択**ユーザー コントロールの追加**します。

2.  型**PhoneNumberBox**名 をクリックします**追加**します。

     **PhoneNumberBox**コントロールに追加されます**ソリューション エクスプ ローラー**、され、デザイナーが開きます。

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox コントロールをデザインします。

このチュートリアルでは、既存<xref:System.Windows.Forms.MaskedTextBox>を作成する、 **PhoneNumberBox**コントロール。

1.  ドラッグ、<xref:System.Windows.Forms.MaskedTextBox>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。

2.  スマート タグの選択、<xref:System.Windows.Forms.MaskedTextBox>だけにドラッグすると、および選択**マスクの設定**します。

3.  選択**電話番号**で、**定型入力** ダイアログ ボックスをクリックします**ok**マスクを設定します。

## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。

単純データ バインディングをサポートするをコントロールには実装、 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  スイッチ、 **PhoneNumberBox**コントロールをコード ビューにします。 (上、**ビュー** ] メニューの [選択**コード**)。

2.  コードに置き換えます、 **PhoneNumberBox**次。

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。

このステップでは、**データ ソースの構成**データ ソースを作成するウィザードがに基づいて、 `Customers` Northwind サンプル データベース内のテーブル。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースのセットアップについては、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)します。

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソースの構成**ウィザード。

3.  **データ ソースの種類を選択**] ページで、[**データベース**、順にクリックします**次**します。

4.  **データ接続の選択** ページで、次のいずれかを実行します。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。

5.  データベースにパスワードが必要な場合をクリックして、機密データを含めるオプションを選択**次**します。

6.  **接続文字列をアプリケーション構成ファイルに保存**] ページで [**次**します。

7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。

8.  選択、`Customers`テーブル、およびクリックして**完了**。

     **NorthwindDataSet**がプロジェクトに追加し、`Customers`テーブルに表示されます、**データ ソース**ウィンドウ。

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>PhoneNumberBox コントロールを使用して、phone 列を設定します。

内で、**データソース**ウィンドウで、フォームに項目をドラッグする前に作成するコントロールを設定することができます。

1.  開いている**Form1**デザイナー。

2.  展開、**顧客**内のノード、**データソース**ウィンドウ。

3.  ドロップダウン矢印をクリックして、**顧客**ノード選択**詳細**コントロール リストから。

4.  ドロップダウン矢印をクリックして、**電話**列選択**カスタマイズ**します。

5.  選択、 **PhoneNumberBox**の一覧から**関連付けられたコントロール**で、**データ UI カスタマイズ オプション** ダイアログ ボックス。

6.  ドロップダウン矢印をクリックして、**電話**列選択**PhoneNumberBox**します。

## <a name="add-controls-to-the-form"></a>コントロールをフォームに追加します。

項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウから、フォームにします。

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