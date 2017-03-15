---
title: "チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ バインド, ユーザー コントロール"
  - "LookupBindingPropertiesAttribute クラス, 例"
  - "ユーザー コントロール [Visual Basic], 作成"
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成
フォームにデータを表示する場合は、ツールボックスから既存のコントロールを選択するか、またはアプリケーションが標準コントロールでは提供できない機能を必要とする場合は、カスタム コントロールを記述できます。  このチュートリアルでは、<xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。  <xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装するコントロールには、データにバインドできるプロパティを 3 つ含めることができます。  このようなコントロールは、<xref:System.Windows.Forms.ComboBox> に似ています。  
  
 コントロールの作成の詳細については、「[デザイン時の Windows フォーム コントロールの開発](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)」を参照してください。  
  
 データ バインディングのシナリオで使用するためのコントロールを作成するときは、次のいずれかのデータ バインド属性を実装する必要があります。  
  
|データ バインド属性の使用|  
|-------------------|  
|単一のデータ列またはプロパティを表示する <xref:System.Windows.Forms.TextBox> のような <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を簡単なコントロールに実装します。  詳細については、「[チュートリアル: 単純データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)」を参照してください。|  
|データの一覧またはテーブルを表示する <xref:System.Windows.Forms.DataGridView> のような <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> をコントロールに実装します。  詳細については、「[チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)」を参照してください。|  
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.Windows.Forms.ComboBox> のような <xref:System.ComponentModel.LookupBindingPropertiesAttribute> をコントロールに実装します。  このチュートリアルでは、このプロセスについて説明します。|  
  
 このチュートリアルでは、2 つのテーブルのデータにバインドする検索コントロールを作成します。  この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。  この検索コントロールは `Orders` テーブルの `CustomerID` フィールドにバインドされます。  コントロールは、この値を使用して `Customers` テーブルの `CompanyName` を検索します。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新しい **Windows アプリケーション**を作成します。  
  
-   新しい**ユーザー コントロール**をプロジェクトに追加します。  
  
-   ユーザー コントロールをビジュアルに設計します。  
  
-   `LookupBindingProperty` 属性を実装します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、データセットを作成します。  
  
-   **\[データ ソース\]** ウィンドウで **Orders** テーブルの **\[CustomerID\]** 列が新しいコントロールを使用するように設定します。  
  
-   フォームを作成して、新しいコントロールにデータを表示します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション**を作成します。  
  
#### 新しい Windows プロジェクトを作成するには  
  
1.  Visual Studio の **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  プロジェクトに LookupControlWalkthrough という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **LookupControlWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## プロジェクトへのユーザー コントロールの追加  
 このチュートリアルでは**ユーザー コントロール**から検索コントロールを作成するので、**ユーザー コントロール**の項目を **LookupControlWalkthrough** プロジェクトに追加します。  
  
#### プロジェクトにユーザー コントロールを追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[ユーザー コントロールの追加\]** をクリックします。  
  
2.  **\[ファイル名\]** 領域に「`LookupBox`」と入力し、**\[追加\]** をクリックします。  
  
     **LookupBox** コントロールが **ソリューション エクスプローラー**に追加され、デザイナーが開きます。  
  
## LookupBox コントロールの設計  
  
#### LookupBox コントロールを設計するには  
  
-   **ツールボックス**からユーザー コントロールのデザイン サーフェイスに <xref:System.Windows.Forms.ComboBox> をドラッグします。  
  
## 必要なデータ バインディング属性の追加  
 データ バインディングをサポートする検索コントロールには、<xref:System.ComponentModel.LookupBindingPropertiesAttribute> を実装できます。  
  
#### LookupBindingProperties 属性を実装するには  
  
1.  **LookupBox** コントロールをコード ビューに切り替えます。  **\[表示\]** メニューの **\[コード\]** をクリックします。  
  
2.  `LookupBox` のコードを次のコードで置き換えます。  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-cs[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
## データベースからのデータ ソースの作成  
 この手順では、**データ ソース構成ウィザード**を使用して、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルに基づいてデータ ソースを作成します。  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
#### データ ソースを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を起動します。  
  
3.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         または  
  
    -   **\[新しい接続\]** を選択して **\[接続の追加\] または \[接続の変更\]** ダイアログ ボックスを表示します。  
  
5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**\[次へ\]** をクリックします。  
  
6.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
8.  `Customers` テーブルと `Orders` テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに `Customers` テーブルと `Orders` テーブルが表示されます。  
  
## LookupBox コントロールを使用するように Orders テーブルの \[CustomerID\] 列を設定する  
 **\[データ ソース\]** ウィンドウでは、フォームにコントロールをドラッグする前に作成するコントロールを設定できます。  
  
#### \[CustomerID\] 列を LookupBox コントロールにバインドするように設定するには  
  
1.  デザイナーで **Form1** を開きます。  
  
2.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
3.  **\[Fax\]** 列の下の **\[Customers\]** 列にある **\[Orders\]** ノードを展開します。  
  
4.  **\[Orders\]** ノードのドロップダウン矢印をクリックし、コントロール一覧の **\[Details\]** を選択します。  
  
5.  **\[Orders\]** ノードの **\[CustomerID\]** 列のドロップダウン矢印をクリックし、**\[Customize\]** をクリックします。  
  
6.  **\[データ UI カスタマイズ オプション\]** ダイアログ ボックスの **\[関連付けられたコントロール\]** の一覧の **\[LookupBox\]** を選択します。  
  
7.  **\[OK\]** をクリックします。  
  
8.  **\[CustomerID\]** 列のドロップダウン矢印をクリックし、**\[LookupBox\]** をクリックします。  
  
## フォームへのコントロールの追加  
 **\[データ ソース\]** ウィンドウから **Form1** に項目をドラッグして、データ バインディング コントロールを作成します。  
  
#### Windows フォームにデータ バインディング コントロールを作成するには  
  
-   **\[データ ソース\]** ウィンドウから Windows フォームに **\[Orders\]** ノードをドラッグし、**LookupBox** コントロールを使用して `CustomerID` 列にデータが表示されていることを確認します。  
  
## Customers テーブルから CompanyName を検索するためにコントロールをバインドする  
  
#### 検索バインドをセットアップするには  
  
-   **\[データ ソース\]** ウィンドウでメインの **\[Customers\]** ノードを選択し、**Form1** の **CustomerIDLookupBox** 内のコンボ ボックスにドラッグします。  
  
     これによって、`Orders` テーブルの `CustomerID` 値を維持しながら、`Customers` テーブルの `CompanyName` を表示するためのデータ バインディングがセットアップされます。  詳細については、「[方法: Windows フォーム アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-windows-forms-applications.md)」を参照してください。  
  
## アプリケーションの実行  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
-   レコード間を移動し、`LookupBox` コントロールに `CompanyName` が表示されることを確認します。  
  
## 参照  
 [\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)