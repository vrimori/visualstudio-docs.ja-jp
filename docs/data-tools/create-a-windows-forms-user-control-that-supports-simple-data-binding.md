---
title: 単純データ バインディングをサポートするユーザー コントロールを作成 |Microsoft ドキュメント
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: edfa94a6ca1bdc4fc8a5e9353505da4354b126ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>単純データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成します。
Windows アプリケーションでフォームにデータを表示する場合から既存のコントロールを選択できます、**ツールボックス**、またはアプリケーションが標準コントロールで利用できない機能に必要な場合は、カスタム コントロールを作成することができます。 このチュートリアルでは、<xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールを作成する方法を示します。 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールには、データにバインドできるプロパティを 1 つ含めることができます。 このようなコントロールは、<xref:System.Windows.Forms.TextBox> や <xref:System.Windows.Forms.CheckBox> に似ています。  
  
 コントロールの作成の詳細については、次を参照してください。[デザイン時に Windows フォーム コントロールの開発](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)です。  
  
 データ バインディングのシナリオで使用するためのコントロールを作成するときに、次のデータ バインディング属性の 1 つを実装する必要があります。  
  
|データ バインディング属性の使用方法|  
|-----------------------------------|  
|単一のデータ列またはプロパティを表示する <xref:System.ComponentModel.DefaultBindingPropertyAttribute> のような <xref:System.Windows.Forms.TextBox> を簡単なコントロールに実装します。 このチュートリアルでは、このプロセスについて説明します。|  
|データの一覧またはテーブルを表示する <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> のような <xref:System.Windows.Forms.DataGridView> をコントロールに実装します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成する](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)です。|  
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.ComponentModel.LookupBindingPropertiesAttribute> のような <xref:System.Windows.Forms.ComboBox> をコントロールに実装します。 詳細については、次を参照してください。[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。|  
  
 このチュートリアルでは、テーブルの単一の列のデータを表示する簡単なコントロールを作成します。 この例では、Northwind サンプル データベースの `Phone` テーブルの `Customers` 列を使用します。 単純なユーザー コントロールを使用して、標準の電話番号形式でお客様の電話番号を表示するが、<xref:System.Windows.Forms.MaskedTextBox>および電話番号をマスクを設定します。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新しい**Windows フォーム アプリケーション**です。  
  
-   新しい**ユーザー コントロール**をプロジェクトにします。  
  
-   ユーザー コントロールをビジュアルに設計します。  
  
-   `DefaultBindingProperty` 属性を実装します。  
  
-   使用してデータセットを作成、**データ ソース構成**ウィザード。  
  
-   設定、 **Phone**内の列、**データソース**新しいコントロールを使用するウィンドウです。  
  
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
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**SimpleControlWalkthrough**を選択し**OK**です。 
  
     **SimpleControlWalkthrough**プロジェクトが作成され、追加する**ソリューション エクスプ ローラー**です。  
  
## <a name="add-a-user-control-to-the-project"></a>ユーザー コントロールをプロジェクトに追加します。  
 このチュートリアルからの単純データ バインド可能なコントロールを作成、**ユーザー コントロール**、ため、追加、**ユーザー コントロール**項目を**SimpleControlWalkthrough**プロジェクト。  
  
#### <a name="to-add-a-user-control-to-the-project"></a>プロジェクトにユーザー コントロールを追加するには  
  
1.  **プロジェクト**] メニューの [選択**ユーザー コントロールの追加**です。  
  
2.  型`PhoneNumberBox`名領域およびクリックで**追加**です。  
  
     **PhoneNumberBox**コントロールが**ソリューション エクスプ ローラー**、され、デザイナーが開きます。  
  
## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox コントロールをデザインします。  
 このチュートリアルでは、既存の <xref:System.Windows.Forms.MaskedTextBox> を展開して `PhoneNumberBox` コントロールを作成します。  
  
#### <a name="to-design-the-phonenumberbox-control"></a>PhoneNumberBox コントロールを設計するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.MaskedTextBox>から、**ツールボックス**ユーザー コントロールのデザイン サーフェイスにします。  
  
2.  スマート タグを選択、<xref:System.Windows.Forms.MaskedTextBox>だけにドラッグすると、および選択**マスクの設定**です。  
  
3.  選択**電話番号**で、**定型入力** ダイアログ ボックスをクリック**ok**マスクを設定します。  
  
## <a name="add-the-required-data-binding-attribute"></a>必要なデータ バインディング属性を追加します。  
 データ バインディングをサポートする簡単なコントロールに対しては <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装します。  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>DefaultBindingProperty 属性を実装するには  
  
1.  `PhoneNumberBox` コントロールをコード ビューに切り替えます。 (上、**ビュー** ] メニューの [選択**コード**)。  
  
2.  `PhoneNumberBox` のコードを次のコードで置き換えます。  
  
     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。  
 このステップでは、**データ ソース構成**データ ソースを作成するウィザードがに基づいて、 `Customers` Northwind サンプル データベース内のテーブルです。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースをセットアップする方法については、次を参照してください。[する方法: サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)です。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]**をクリックします。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成**ウィザード。  
  
3.  **データ ソースの種類を選択**] ページで、[**データベース**、順にクリック**次**です。  
  
4.  **データ接続の選択** ページで、次のいずれかの操作します。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
    -   選択**新しい接続**を起動する、**接続接続の追加/変更** ダイアログ ボックス。  
  
5.  データベースは、パスワードを必要とする場合は、機密データを含めるし、をクリックするオプションを選択**次**です。  
  
6.  **接続文字列をアプリケーション構成ファイルに保存** ページで、をクリックして**次**です。  
  
7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。  
  
8.  選択、`Customers`テーブル、およびクリックして**完了**です。  
  
     **NorthwindDataSet**をプロジェクトに追加され、`Customers`テーブルに表示されます、**データ ソース**ウィンドウです。  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>PhoneNumberBox コントロールを使用して、phone 列を設定します。  
 内で、**データソース**ウィンドウ、フォームに項目をドラッグする前に作成されるコントロールを設定できます。  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>[Phone] 列を PhoneNumberBox コントロールにバインドするように設定するには  
  
1.  開いている**Form1**デザイナーでします。  
  
2.  展開、**顧客**内のノード、**データソース**ウィンドウです。  
  
3.  ドロップダウン矢印をクリックして、**顧客** ノードを選択し、**詳細**コントロール リストからです。  
  
4.  ドロップダウン矢印をクリックして、 **Phone**  列を選択し、**カスタマイズ**です。  
  
5.  選択、 **PhoneNumberBox**の一覧から**関連付けられたコントロール**で、**データ UI カスタマイズ オプション** ダイアログ ボックス。  
  
6.  ドロップダウン矢印をクリックして、 **Phone**  列を選択して**PhoneNumberBox**です。  
  
## <a name="add-controls-to-the-form"></a>フォームにコントロールを追加します。  
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウからフォームにします。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには  
  
-   メインのドラッグ**顧客**からノード、**データ ソース**ウィンドウから、フォームにいることを確認し、`PhoneNumberBox`内のデータを表示するコントロールを使用、`Phone`列です。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
## <a name="run-the-application"></a>アプリケーションの実行  
  
#### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。 次の手順として、一般的には、次のようなことを実行します。  
  
-   他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。  
  
-   より複雑なデータ バインディングのシナリオをサポートするコントロールを作成します。 詳細については、次を参照してください。[複合データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成する](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)と[ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールを作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
