---
title: "チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成 | Microsoft Docs"
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
  - "データ バインド, 複合"
  - "データ バインド, ユーザー コントロール"
  - "ユーザー コントロール [Visual Studio], 複合データ バインド"
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: 複合データ バインドをサポートする Windows フォーム ユーザー コントロールの作成
Windows アプリケーションのフォームにデータを表示する場合は、**\[ツールボックス\]** から既存のコントロールを選択するか、またはアプリケーションが標準コントロールでは提供できない機能を必要とする場合は、カスタム コントロールを記述できます。  このチュートリアルでは、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールを作成する方法を示します。  <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装するコントロールには、データにバインドできる `DataSource` プロパティと `DataMember` プロパティが含まれます。  このようなコントロールは、<xref:System.Windows.Forms.DataGridView> や <xref:System.Windows.Forms.ListBox> に似ています。  
  
 コントロールの作成の詳細については、「[デザイン時の Windows フォーム コントロールの開発](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)」を参照してください。  
  
 データ バインディングのシナリオで使用するためのコントロールを作成するときは、次のいずれかのデータ バインド属性を実装する必要があります。  
  
|データ バインド属性の使用|  
|-------------------|  
|単一のデータ列またはプロパティを表示する <xref:System.Windows.Forms.TextBox> のような <xref:System.ComponentModel.DefaultBindingPropertyAttribute> を簡単なコントロールに実装します。  詳細については、「[チュートリアル: 単純データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)」を参照してください。|  
|データの一覧またはテーブルを表示する <xref:System.Windows.Forms.DataGridView> のような <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> をコントロールに実装します。  このチュートリアルでは、このプロセスについて説明します。|  
|データの一覧またはテーブルを表示しますが、単一の列またはプロパティを表示する必要もある <xref:System.Windows.Forms.ComboBox> のような <xref:System.ComponentModel.LookupBindingPropertiesAttribute> をコントロールに実装します。  詳細については、「[チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)」を参照してください。|  
  
 このチュートリアルでは、テーブルからのデータ行を表示する複合コントロールを作成します。  この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。  複合ユーザー コントロールは、カスタム コントロールの <xref:System.Windows.Forms.DataGridView> で Customers テーブルを表示します。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新しい **Windows アプリケーション**を作成します。  
  
-   新しい**ユーザー コントロール**をプロジェクトに追加します。  
  
-   ユーザー コントロールをビジュアルに設計します。  
  
-   `ComplexBindingProperty` 属性を実装します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、データセットを作成します。  
  
-   [ウィンドウ](../Topic/Data%20Sources%20Window.md)の **Customers** テーブルが新しい複合コントロールを使用するように設定します。  
  
-   **\[データ ソース\] ウィンドウ**から **Form1** に新しいコントロールをドラッグして追加します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション**を作成します。  
  
#### 新しい Windows プロジェクトを作成するには  
  
1.  Visual Studio の **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  プロジェクトに ComplexControlWalkthrough という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **ComplexControlWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## プロジェクトへのユーザー コントロールの追加  
 このチュートリアルでは**ユーザー コントロール**からデータ バインディング可能な複合コントロールを作成するので、**ユーザー コントロール**の項目をプロジェクトに追加する必要があります。  
  
#### プロジェクトにユーザー コントロールを追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[ユーザー コントロールの追加\]** を選択します。  
  
2.  **\[ファイル名\]** 領域に「ComplexDataGridView」と入力し、**\[追加\]** をクリックします。  
  
     **ComplexDataGridView** コントロールが **ソリューション エクスプローラー**に追加され、デザイナーが開きます。  
  
## ComplexDataGridView コントロールの設計  
 この手順では、ユーザー コントロールに <xref:System.Windows.Forms.DataGridView> を追加します。  
  
#### ComplexDataGridView コントロールを設計するには  
  
-   **ツールボックス**からユーザー コントロールのデザイン サーフェイスに <xref:System.Windows.Forms.DataGridView> をドラッグします。  
  
## 必要なデータ バインディング属性の追加  
 データ バインディングをサポートする複合コントロールには、<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> を実装できます。  
  
#### ComplexBindingProperties 属性を実装するには  
  
1.  **ComplexDataGridView** コントロールをコード ビューに切り替えます。  **\[表示\]** メニューの **\[コード\]** を選択します。  
  
2.  `ComplexDataGridView` のコードを次のコードで置き換えます。  
  
     [!code-cs[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
## データベースからのデータ ソースの作成  
 この手順では、**データ ソース構成ウィザード**を使用して、Northwind サンプル データベースの `Customers` テーブルに基づいてデータ ソースを作成します。  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
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
  
8.  `Customers` テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに `Customers` テーブルが表示されます。  
  
## ComplexDataGridView コントロールを使用するように Customers テーブルを設定する  
 **\[データ ソース\]** ウィンドウでは、フォームにコントロールをドラッグする前に作成するコントロールを設定できます。  
  
#### Customers テーブルを ComplexDataGridView コントロールにバインドするように設定するには  
  
1.  デザイナーで **Form1** を開きます。  
  
2.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
3.  **\[Customers\]** ノードのドロップダウン矢印をクリックし、**\[カスタマイズ\]** をクリックします。  
  
4.  **\[データ UI カスタマイズ オプション\]** ダイアログ ボックスの **\[関連付けられたコントロール\]** の一覧の **\[ComplexDataGridView\]** を選択します。  
  
5.  `Customers` テーブルのドロップダウン矢印をクリックし、コントロール リストから **ComplexDataGridView** を選択します。  
  
## フォームへのコントロールの追加  
 **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### フォームにデータ バインド コントロールを作成するには  
  
-   **\[データ ソース\]** ウィンドウからフォームにメインの **\[Customers\]** ノードをドラッグし、**ComplexDataGridView** コントロールを使用してテーブルのデータが表示されていることを確認します。  
  
## アプリケーションの実行  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
## 次の手順  
 アプリケーションの要件に応じて、データ バインディングをサポートするコントロールの作成後に、追加の操作を実行できます。  次の手順として、一般的には、次のようなことを実行します。  
  
-   他のアプリケーションで再利用できるように、コントロール ライブラリにカスタム コントロールを配置します。  
  
-   検索のシナリオをサポートするコントロールを作成します。  詳細については、「[チュートリアル: 検索データ バインドをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)」を参照してください。  
  
## 参照  
 [\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)   
 [Windows フォーム コントロール](../Topic/Windows%20Forms%20Controls.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)