---
title: "チュートリアル: 単純データ バインドをサポートする Windows フォーム ユーザー コントロールの作成 | Microsoft Docs"
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
  - "カスタム コントロール [Visual Studio], [データ ソース] ウィンドウ"
  - "[データ ソース] ウィンドウ, コントロール"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: 単純データ バインドをサポートする Windows フォーム ユーザー コントロールの作成
Windows アプリケーションのフォームにデータを表示する場合は、**\[ツールボックス\]** から既存のコントロールを選択するか、またはアプリケーションが標準コントロールでは提供できない機能を必要とする場合は、カスタム コントロールを記述できます。  このチュートリアルでは、<xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールを作成する方法を示します。  <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装するコントロールには、データにバインドできるプロパティを 1 つ含めることができます。  このようなコントロールは、<xref:System.Windows.Forms.TextBox> や <xref:System.Windows.Forms.CheckBox> に似ています。  
  
 コントロールの作成の詳細については、「[デザイン時の Windows フォーム コントロールの開発](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)」を参照してください。  
  
 データ バインディングのシナリオで使用するためのコントロールを作成するときは、次のいずれかのデータ バインド属性を実装する必要があります。  
  
|データ バインド属性の使用|  
|-------------------|  
|単一のデータ列またはプロパティを表示する <xref:System.Windows.Forms.TextBox> のような <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を簡単なコントロールに実装します。  このチュートリアルでは、このプロセスについて説明します。|  
|データの一覧またはテーブルを表示する <xref:System.Windows.Forms.DataGridView> のような <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> をコントロールに実装します。  詳細については、「[チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)」を参照してください。|  
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.Windows.Forms.ComboBox> のような <xref:System.ComponentModel.LookupBindingPropertiesAttribute> をコントロールに実装します。  詳細については、「[チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)」を参照してください。|  
  
 このチュートリアルでは、テーブルの単一の列のデータを表示する簡単なコントロールを作成します。  この例では、Northwind サンプル データベースの `Customers` テーブルの `Phone` 列を使用します。  この簡単なユーザー コントロールは、<xref:System.Windows.Forms.MaskedTextBox> を使用し、電話番号にマスクを設定して、顧客の電話番号を標準の電話番号形式で表示します。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新しい **Windows アプリケーション**を作成します。  
  
-   新しい**ユーザー コントロール**をプロジェクトに追加します。  
  
-   ユーザー コントロールをビジュアルに設計します。  
  
-   `DefaultBindingProperty` 属性を実装します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、データセットを作成します。  
  
-   **\[データ ソース\]** ウィンドウで **\[Phone\]** 列が新しいコントロールを使用するように設定します。  
  
-   フォームを作成して、新しいコントロールにデータを表示します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション**を作成します。  
  
#### 新しい Windows プロジェクトを作成するには  
  
1.  Visual Studio の **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  プロジェクトに **SimpleControlWalkthrough** という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **SimpleControlWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## プロジェクトへのユーザー コントロールの追加  
 このチュートリアルでは**ユーザー コントロール**からデータ バインディング可能な簡単なコントロールを作成するので、**ユーザー コントロール**の項目を **SimpleControlWalkthrough** プロジェクトに追加します。  
  
#### プロジェクトにユーザー コントロールを追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[ユーザー コントロールの追加\]** を選択します。  
  
2.  \[ファイル名\] 領域に「`PhoneNumberBox`」と入力し、**\[追加\]** をクリックします。  
  
     **PhoneNumberBox** コントロールが **ソリューション エクスプローラー**に追加され、デザイナーが開きます。  
  
## PhoneNumberBox コントロールの設計  
 このチュートリアルでは、既存の <xref:System.Windows.Forms.MaskedTextBox> を展開して `PhoneNumberBox` コントロールを作成します。  
  
#### PhoneNumberBox コントロールを設計するには  
  
1.  **ツールボックス**からユーザー コントロールのデザイン サーフェイスに <xref:System.Windows.Forms.MaskedTextBox> をドラッグします。  
  
2.  ドラッグした <xref:System.Windows.Forms.MaskedTextBox> のスマート タグを選択し、**\[マスクの設定\]** を選択します。  
  
3.  **\[定型入力\]**ダイアログ ボックスで **\[電話番号\]** を選択し、**\[OK\]** をクリックしてマスクを設定します。  
  
## 必要なデータ バインディング属性の追加  
 データ バインディングをサポートする簡単なコントロールに対しては <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を実装します。  
  
#### DefaultBindingProperty 属性を実装するには  
  
1.  `PhoneNumberBox` コントロールをコード ビューに切り替えます。  **\[表示\]** メニューの **\[コード\]** をクリックします。  
  
2.  `PhoneNumberBox` のコードを次のコードで置き換えます。  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
## データベースからのデータ ソースの作成  
 この手順では、**データ ソース構成ウィザード**を使用して、Northwind サンプル データベースの `Customers` テーブルに基づいてデータ ソースを作成します。  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
#### データ ソースを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を起動します。  
  
3.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         Or  
  
    -   **\[新しい接続\]** を選択して **\[接続の追加\] または \[接続の変更\]** ダイアログ ボックスを表示します。  
  
5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**\[次へ\]** をクリックします。  
  
6.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
8.  `Customers` テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに `Customers` テーブルが表示されます。  
  
## PhoneNumberBox コントロールを使用するように \[Phone\] 列を設定する  
 **\[データ ソース\]** ウィンドウでは、フォームにコントロールをドラッグする前に作成するコントロールを設定できます。  
  
#### \[Phone\] 列を PhoneNumberBox コントロールにバインドするように設定するには  
  
1.  デザイナーで **Form1** を開きます。  
  
2.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
3.  **\[Customers\]** ノードのドロップダウン矢印をクリックし、コントロール リストの **\[Details\]** を選択します。  
  
4.  **\[Phone\]** 列のドロップダウン矢印をクリックし、**\[Customize\]** をクリックします。  
  
5.  **\[データ UI カスタマイズ オプション\]** ダイアログ ボックスの **\[関連付けられたコントロール\]** の一覧の **\[PhoneNumberBox\]** を選択します。  
  
6.  **\[Phone\]** 列のドロップダウン矢印をクリックし、**\[PhoneNumberBox\]** をクリックします。  
  
## フォームへのコントロールの追加  
 **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### フォームにデータ バインド コントロールを作成するには  
  
-   **\[データ ソース\]** ウィンドウからフォームにメインの **\[Customers\]** ノードをドラッグし、`PhoneNumberBox` コントロールを使用して `Phone` 列にデータが表示されていることを確認します。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォームに表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
## アプリケーションの実行  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
## 次の手順  
 アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。  次の手順として、一般的には、次のようなことを実行します。  
  
-   他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。  
  
-   より複雑なデータ バインディングのシナリオをサポートするコントロールを作成します。  詳細については、「[チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)」および「[チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)」を参照してください。  
  
## 参照  
 [\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)