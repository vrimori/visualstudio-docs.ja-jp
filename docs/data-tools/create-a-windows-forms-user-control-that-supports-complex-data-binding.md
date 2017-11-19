---
title: "データ バインディングを使用する Windows フォーム ユーザー コントロールを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8b23bfe7c30988a80904377e583a5a5f6d4cd2ff
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成します。
Windows アプリケーションでフォームにデータを表示する場合から既存のコントロールを選択できます、**ツールボックス**、またはアプリケーションが標準コントロールで利用できない機能に必要な場合は、カスタム コントロールを作成することができます。 このチュートリアルでは、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールには、データにバインドできる `DataSource` プロパティと `DataMember` プロパティが含まれます。 このようなに似ていますが、<xref:System.Windows.Forms.DataGridView>または<xref:System.Windows.Forms.ListBox>  
  
 コントロールの作成の詳細については、次を参照してください。[デザイン時に Windows フォーム コントロールの開発](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)です。  
  
 データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性のいずれかを実装する必要があります。  
  
|データ バインディング属性の使用方法|  
|-----------------------------------|  
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 詳細については、次を参照してください。[単純データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成する](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)です。|  
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|  
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|  
  
 このチュートリアルでは、テーブルからのデータ行を表示する複合コントロールを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。 複合ユーザー コントロールは、カスタム コントロールの <xref:System.Windows.Forms.DataGridView> で Customers テーブルを表示します。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新しい**Windows フォーム アプリケーション**です。  
  
-   新しい**ユーザー コントロール**をプロジェクトにします。  
  
-   ユーザー コントロールをビジュアルに設計します。  
  
-   `ComplexBindingProperty` 属性を実装します。  
  
-   使用してデータセットを作成、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)です。  
  
-   設定、**顧客**テーブルに、[データ ソース ウィンドウ](add-new-data-sources.md)新しい複雑なコントロールを使用します。  
  
-   ドラッグして、新しいコントロールを追加、**データ ソース ウィンドウ**に**Form1**です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。  
  
1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server のエディションのダウンロード ページ](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。  
  
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
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**ComplexControlWalkthrough**を選択し**OK**です。 
  
     **ComplexControlWalkthrough**プロジェクトが作成され、追加する**ソリューション エクスプ ローラー**です。  
  
## <a name="add-a-user-control-to-the-project"></a>ユーザー コントロールをプロジェクトに追加します。  
 このチュートリアルから複雑なデータ バインド可能なコントロールが作成されるため、**ユーザー コントロール**、追加する必要があります、**ユーザー コントロール**プロジェクト項目です。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加するには  
  
1.  **プロジェクト**] メニューの [選択**ユーザー コントロールの追加**です。  
  
2.  型**ComplexDataGridView**で、**名前**領域およびクリック**追加**です。  
  
     **ComplexDataGridView**コントロールが**ソリューション エクスプ ローラー**、され、デザイナーが開きます。  
  
## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView コントロールをデザインします。  
 この手順では、ユーザー コントロールに <xref:System.Windows.Forms.DataGridView> を追加します。  
  
#### <a name="to-design-the-complexdatagridview-control"></a>ComplexDataGridView コントロールを設計するには  
  
-   ドラッグ、<xref:System.Windows.Forms.DataGridView>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。  
  
## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。  
 データ バインディングをサポートする複合コントロールには、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装できます。  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>ComplexBindingProperties 属性を実装するには  
  
1.  スイッチ、 **ComplexDataGridView**コントロールをコード ビューにします。 (上、**ビュー**メニューの **コード**)。  
  
2.  `ComplexDataGridView` のコードを次のコードで置き換えます。  
  
     [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
## <a name="creating-a-data-source-from-your-database"></a>データベースからデータ ソースの作成  
このステップでは、**データ ソース構成**データ ソースを作成するウィザードがに基づいて、 `Customers` Northwind サンプル データベース内のテーブルです。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成**ウィザード。  
  
3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]**をクリックします。  
  
4.  **データ接続の選択**ページは、次のいずれか。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
    -   選択**新しい接続**を起動する、**接続接続の追加/変更** ダイアログ ボックス。  
  
5.  データベースは、パスワードを必要とする場合は、機密データを含めるし、をクリックするオプションを選択**次**です。  
  
6.  **接続文字列をアプリケーション構成ファイルに保存** ページで、をクリックして**次**です。  
  
7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。  
  
8.  選択、`Customers`テーブル、およびクリックして**完了**です。  
  
     **NorthwindDataSet**をプロジェクトに追加され、`Customers`テーブルに表示されます、**データ ソース**ウィンドウです。  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>ComplexDataGridView コントロールを使用して、Customers テーブルを設定します。  
 内で、**データソース**ウィンドウ、フォームに項目をドラッグする前に作成されるコントロールを設定できます。  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Customers テーブルを ComplexDataGridView コントロールにバインドするように設定するには  
  
1.  開いている**Form1**デザイナーでします。  
  
2.  展開、**顧客**内のノード、**データソース**ウィンドウです。  
  
3.  ドロップダウン矢印をクリックして、**顧客** ノードを選択して**カスタマイズ**です。  
  
4.  選択、 **ComplexDataGridView**の一覧から**関連付けられたコントロール**で、**データ UI カスタマイズ オプション** ダイアログ ボックス。  
  
5.  ドロップダウン矢印をクリックして、`Customers`テーブル、および選択**ComplexDataGridView**コントロール リストからです。  
  
## <a name="add-controls-to-the-form"></a>フォームにコントロールを追加します。  
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウからフォームにします。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには  
  
-   メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウからフォームにします。いることを確認、 **ComplexDataGridView**テーブルのデータを表示するコントロールを使用します。  
  
## <a name="running-the-application"></a>アプリケーションの実行  
  
#### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。 次の手順として、一般的には、次のようなことを実行します。  
  
-   他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。  
  
-   検索のシナリオをサポートするコントロールを作成します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データ ソース ウィンドウからドラッグしたときに作成するコントロールを設定します。](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)
