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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: db8059cf34c2de9a52cda18dd09ce6040bf8d841
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937903"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成します。

Windows アプリケーションでフォームにデータを表示するときにから既存のコントロールを選択することができます、**ツールボックス**、またはアプリケーションが標準のコントロールで使用できない機能に必要な場合は、カスタム コントロールを作成できます。 このチュートリアルでは、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールには、データにバインドできる `DataSource` プロパティと `DataMember` プロパティが含まれます。 このようなコントロールは、<xref:System.Windows.Forms.DataGridView> や <xref:System.Windows.Forms.ListBox> に似ています。

コントロールの作成の詳細については、次を参照してください。 [Windows フォームの開発は、デザイン時にコントロール](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)します。

データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性のいずれかを実装する必要があります。

|データ バインディング属性の使用方法|
| - |
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 詳細については、次を参照してください。[単純データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)です。|
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロール作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|

このチュートリアルでは、テーブルからのデータ行を表示する複合コントロールを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。 複合ユーザー コントロールは、カスタム コントロールの <xref:System.Windows.Forms.DataGridView> で Customers テーブルを表示します。

このチュートリアルでは、次の作業を行う方法について説明します。

- 新規作成**Windows フォーム アプリケーション**します。

- 新しい追加**ユーザー コントロール**をプロジェクトにします。

- ユーザー コントロールをビジュアルに設計します。

- `ComplexBindingProperty` 属性を実装します。

- 使用してデータセットを作成、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)します。

- 設定、**顧客**テーブルに、[データ ソース ウィンドウ](add-new-data-sources.md)新しい複雑なコントロールを使用します。

- 新しいコントロールをドラッグしてから、追加、**データ ソース ウィンドウ**に**Form1**します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1. SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

1. 次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    1. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    1. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。

作成するには、まず、 **Windows フォーム アプリケーション**:

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

1. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

1. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

1. プロジェクトに名前を**ComplexControlWalkthrough**を選び、 **OK**。

    **ComplexControlWalkthrough**プロジェクトを作成するとに追加**ソリューション エクスプ ローラー**します。

## <a name="add-a-user-control-to-the-project"></a>ユーザー コントロールをプロジェクトに追加します。

このチュートリアルから複雑なデータ バインド コントロールが作成されるため、**ユーザー コントロール**、追加、**ユーザー コントロール**をプロジェクトに項目。

1. **プロジェクト**] メニューの [選択**ユーザー コントロールの追加**します。

1. 型**ComplexDataGridView**で、**名前**領域、およびクリック**追加**します。

    **ComplexDataGridView**コントロールに追加されます**ソリューション エクスプ ローラー**、され、デザイナーが開きます。

## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView コントロールをデザインします。

追加する、<xref:System.Windows.Forms.DataGridView>ユーザー コントロールにドラッグ、<xref:System.Windows.Forms.DataGridView>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。

## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。

実装する複雑なデータ バインディングをサポートするをコントロールには、 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. スイッチ、 **ComplexDataGridView**コントロールをコード ビューにします。 (上、**ビュー**メニューの **コード**)。

1. `ComplexDataGridView` のコードを次のコードで置き換えます。

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。

使用して、**データ ソースの構成**データ ソースを作成するウィザードがに基づいて、 `Customers` Northwind サンプル データベース内のテーブル。

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソースの構成**ウィザード。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **データ接続の選択**ページは、次のいずれか。

    - Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    - 選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。

5.  データベースにパスワードが必要な場合をクリックして、機密データを含めるオプションを選択**次**します。

6.  **接続文字列をアプリケーション構成ファイルに保存**] ページで [**次**します。

7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。

8.  選択、`Customers`テーブル、およびクリックして**完了**。

    **NorthwindDataSet**がプロジェクトに追加し、`Customers`テーブルに表示されます、**データ ソース**ウィンドウ。

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>ComplexDataGridView コントロールを使用して Customers テーブルを設定します。

内で、**データソース**ウィンドウで、フォームに項目をドラッグする前に作成するコントロールを設定することができます。

1. 開いている**Form1**デザイナー。

1. 展開、**顧客**内のノード、**データソース**ウィンドウ。

1. ドロップダウン矢印をクリックして、**顧客**ノード選択**カスタマイズ**します。

1. 選択、 **ComplexDataGridView**の一覧から**関連付けられたコントロール**で、**データ UI カスタマイズ オプション** ダイアログ ボックス。

1. ドロップダウン矢印をクリックして、`Customers`テーブル、および選択**ComplexDataGridView**コントロール リストから。

## <a name="add-controls-to-the-form"></a>コントロールをフォームに追加します。

項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウから、フォームにします。 メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウから、フォームにします。 いることを確認、 **ComplexDataGridView**テーブルのデータを表示するコントロールを使用します。

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