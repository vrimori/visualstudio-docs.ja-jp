---
title: データ バインディングを使用する Windows フォーム ユーザー コントロールを作成します。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 8e8a78db0d63edc90cbeb36120cc457edd74d25b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001318"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>複合データ バインディングをサポートする Windows フォーム ユーザー コントロールの作成

Windows アプリケーションのフォームにデータを表示する場合は、**[ツールボックス]** から既存のコントロールを選択するか、またはアプリケーションが標準コントロールでは提供できない機能を必要とする場合は、カスタム コントロールを記述できます。 このチュートリアルでは、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールには、データにバインドできる `DataSource` プロパティと `DataMember` プロパティが含まれます。 このようなコントロールは、<xref:System.Windows.Forms.DataGridView> や <xref:System.Windows.Forms.ListBox> に似ています。

コントロールの作成の詳細については、次を参照してください。 [Windows フォームの開発は、デザイン時にコントロール](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)します。

データ バインディングのシナリオで使用するためのコントロールを作成するときは、次のいずれかのデータ バインディング属性を実装する必要があります。

|データ バインディング属性の使用方法|
| - |
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 詳細については、次を参照してください。[単純データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)です。|
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|

このチュートリアルでは、テーブルからのデータ行を表示する複合コントロールを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。 複合ユーザー コントロールは、カスタム コントロールの <xref:System.Windows.Forms.DataGridView> で Customers テーブルを表示します。

このチュートリアルでは、次の作業を行う方法について説明します。

- 新しい **Windows フォーム アプリケーション**を作成します。

- 新しい**ユーザー コントロール**をプロジェクトに追加します。

- ユーザー コントロールをビジュアルに設計します。

- `ComplexBindingProperty` 属性を実装します。

- 使用してデータセットを作成、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)します。

- 設定、**顧客**テーブルに、[データ ソース ウィンドウ](add-new-data-sources.md#data-sources-window)新しい複雑なコントロールを使用します。

- **[データ ソース]** ウィンドウから **Form1** に新しいコントロールをドラッグして追加します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1. SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

1. 次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    1. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    1. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成する

作成するには、まず、 **Windows フォーム アプリケーション**:

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

1. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

1. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

1. プロジェクトに名前を**ComplexControlWalkthrough**を選び、 **OK**。

    **ComplexControlWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。

## <a name="add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加する

このチュートリアルから複雑なデータ バインド コントロールが作成されるため、**ユーザー コントロール**、追加、**ユーザー コントロール**をプロジェクトに項目。

1. **[プロジェクト]** メニューの **[ユーザー コントロールの追加]** を選択します。

1. **[ファイル名]** 領域に「**ComplexDataGridView**」と入力し、**[追加]** をクリックします。

    **ComplexDataGridView** コントロールが**ソリューション エクスプローラー**に追加され、デザイナーが開きます。

## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView コントロールをデザインします。

追加する、<xref:System.Windows.Forms.DataGridView>ユーザー コントロールにドラッグ、<xref:System.Windows.Forms.DataGridView>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。

## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。

データ バインディングをサポートする複合コントロールには、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装できます。

1. **ComplexDataGridView** コントロールをコード ビューに切り替えます  (**[表示]** メニューの **[コード]** を選択します)。

1. `ComplexDataGridView` のコードを次のコードで置き換えます。

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。

使用して、**データ ソースの構成**データ ソースを作成するウィザードがに基づいて、 `Customers` Northwind サンプル データベース内のテーブル。

1.  開くには、**データ ソース**ウィンドウで、**データ**] メニューのをクリックして **[データ ソースの**します。

2.  **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成**ウィザードを起動します。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。

    - Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    - **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを表示します。

5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**[次へ]** をクリックします。

6.  **[アプリケーション構成ファイルに接続文字列を保存]** ページで、**[次へ]** をクリックします。

7.  **[データベース オブジェクトの選択]** ページで、**[テーブル]** ノードを展開します。

8.  `Customers` テーブルを選択し、**[完了]** をクリックします。

    プロジェクトに **NorthwindDataSet** が追加され、**[データ ソース]** ウィンドウに `Customers` テーブルが表示されます。

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>ComplexDataGridView コントロールを使用して Customers テーブルを設定します。

**[データ ソース]** ウィンドウでは、フォームにコントロールをドラッグする前に作成するコントロールを設定できます。

1. デザイナーで **Form1** を開きます。

1. **[データ ソース]** ウィンドウの **[Customers]** ノードを展開します。

1. **[Customers]** ノードのドロップダウン矢印をクリックし、**[カスタマイズ]** をクリックします。

1. **[データ UI カスタマイズ オプション]** ダイアログ ボックスの **[関連付けられたコントロール]** の一覧の **[ComplexDataGridView]** を選択します。

1. `Customers` テーブルのドロップダウン矢印をクリックし、コントロール リストから **ComplexDataGridView** を選択します。

## <a name="add-controls-to-the-form"></a>コントロールをフォームに追加します。

**[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。 **[データ ソース]** ウィンドウからフォームにメインの **[Customers]** ノードをドラッグします。 いることを確認、 **ComplexDataGridView**テーブルのデータを表示するコントロールを使用します。

## <a name="run-the-application"></a>アプリケーションの実行

**F5** キーを押してアプリケーションを実行します。

## <a name="next-steps"></a>次の手順

アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。 次の手順として、一般的には、次のようなことを実行します。

- 他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。

- 検索のシナリオをサポートするコントロールを作成します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)