---
title: "チュートリアル : 同時実行例外の処理 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "同時実行制御, 例外"
  - "同時実行制御, チュートリアル"
  - "データの同時実行, チュートリアル"
  - "データセット [Visual Basic], エラー"
  - "例外処理, 同時実行の問題"
  - "更新 (データセットを), エラー"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル : 同時実行例外の処理
2 人のユーザーが同じデータベースの同じデータを同時に変更しようとすると、同時実行例外 \(<xref:System.Data.DBConcurrencyException>\) が発生します。  このチュートリアルでは、<xref:System.Data.DBConcurrencyException> をキャッチし、エラーが発生した行を特定し、それに対処する方法の 1 つを示す、Windows アプリケーションを作成します。  
  
 ここでは次の手順を実行します。  
  
1.  新しい **Windows アプリケーション** プロジェクトを作成します。  
  
2.  Northwind `Customers` テーブルに基づいて、新しいデータセットを作成します。  
  
3.  データを表示する <xref:System.Windows.Forms.DataGridView> を備えたフォームを作成します。  
  
4.  Northwind データベースの `Customers` テーブルからデータセットにデータを読み込みます。  
  
5.  データセットにデータを読み込んだ後で、Visual Studio の [Visual Database Tools](http://msdn.microsoft.com/ja-jp/6b145922-2f00-47db-befc-bf351b4809a1) を使用して `Customers` データ テーブルに直接アクセスし、レコードを変更します。  
  
6.  次にフォームで、同じレコードを別の値に変更し、データセットを更新し、変更内容をデータベースに書き込もうとします。これにより、同時実行エラーが発生します。  
  
7.  エラーをキャッチし、操作を継続してデータベースを更新するか、または更新をキャンセルするかを判断できるように、レコードの異なるバージョンを表示します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスして更新を実行するためのアクセス許可。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 新規プロジェクトの作成  
 新しい Windows アプリケーションの作成からチュートリアルを開始します。  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  **\[プロジェクトの種類\]** ペインでプログラミング言語を選択します。  
  
3.  **\[テンプレート\]** ペインの **\[Windows アプリケーション\]** をクリックします。  
  
4.  プロジェクトに `ConcurrencyWalkthrough` という名前を付け、**\[OK\]** をクリックします。  
  
     Visual Studio によって**ソリューション エクスプローラー**にプロジェクトが追加され、デザイナーに新しいフォームが表示されます。  
  
## Northwind データセットの作成  
 ここでは、`NorthwindDataSet` という名前のデータセットを作成します。  
  
#### NorthwindDataSet を作成するには  
  
1.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックします。  
  
     [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png) が表示されます。  
  
2.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックします。  
  
3.  利用可能な接続の一覧から Northwind サンプル データベースへの接続を選択するか、または接続の一覧に使用できる接続がない場合は **\[新しい接続\]** をクリックします。  
  
    > [!NOTE]
    >  ローカル データベース ファイルに接続する場合は、プロジェクトにファイルを追加するかどうかをたずねるメッセージが表示されたときに **\[いいえ\]** をクリックします。  
  
4.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
5.  **\[テーブル\]** ノードを展開し、`Customers` テーブルを選択します。  既定のデータセット名は、`NorthwindDataSet` です。  
  
6.  **\[完了\]** をクリックして、プロジェクトにデータセットを追加します。  
  
## データ バインド DataGridView コントロールの作成  
 ここでは、**\[データ ソース\]** ウィンドウから Windows フォームに **Customers** 項目をドラッグして、<xref:System.Windows.Forms.DataGridView> を作成します。  
  
#### Customers テーブルにバインドする DataGridView コントロールを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックして **\[データ ソース\]** ウィンドウを開きます。  
  
2.  **\[データ ソース\]** ウィンドウの **\[NorthwindDataSet\]** ノードを展開し、**Customers** テーブルを選択します。  
  
3.  テーブル ノードの下向きの矢印をクリックし、ドロップダウン リストの **\[DataGridView\]** を選択します。  
  
4.  テーブルをフォームの空の領域にドラッグします。  
  
     `CustomersDataGridView` という名前の <xref:System.Windows.Forms.DataGridView> コントロールと `CustomersBindingNavigator` という名前の <xref:System.Windows.Forms.BindingNavigator> が、フォームに追加されます。このフォームは、<xref:System.Windows.Forms.BindingSource> にバインドされ、さらに <xref:System.Windows.Forms.BindingSource> は `NorthwindDataSet` 内の `Customers` テーブルにバインドされます。  
  
## チェックポイント  
 フォームをテストして、ここまでの設定が期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
     フォームは、`Customers` テーブルのデータが読み込まれた状態で <xref:System.Windows.Forms.DataGridView> コントロールに表示されます。  
  
2.  **\[デバッグ\]** メニューの **\[デバッグの停止\]** をクリックします。  
  
## 同時実行エラーの処理  
 エラーを処理する方法は、アプリケーションを管理するそれぞれのビジネス ルールによって異なります。  ここでは、同時実行違反が起きた後で、次の同時実行エラーの対処方法を例として実行します。  
  
 アプリケーションは、ユーザーに対してレコードのバージョンを 3 つ用意します。  
  
-   データベース内の現在のレコード。  
  
-   データセットに読み込まれた元のレコード。  
  
-   データセット内の提案された変更。  
  
 ユーザーは、提案されたバージョンでデータベースを上書きするか、更新をキャンセルし、データベースから新しい値をデータセットに再読み込みできます。  
  
#### 同時実行エラーを処理できるようにするには  
  
1.  カスタム エラー ハンドラーの作成  
  
2.  ユーザーに対する選択肢の表示  
  
3.  ユーザーの応答の処理  
  
4.  更新の再送、またはデータセット内のデータのリセット  
  
### 同時実行例外を処理するコードの追加  
 更新の実行を試みると例外が発生する場合、通常は、発生した例外によって提供される情報に対して何らかの対処を行います。  
  
 ここでは、データベースを更新しようとし、生成される可能性がある <xref:System.Data.DBConcurrencyException> およびその他の例外を処理するコードを追加します。  
  
> [!NOTE]
>  このチュートリアルの後半で、`CreateMessage` メソッドと `ProcessDialogResults` メソッドを追加します。  
  
##### 同時実行エラー用のエラー処理を追加するには  
  
1.  `Form1_Load` メソッドの下に次のコードを追加します。  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  次のように `CustomersBindingNavigatorSaveItem_Click` メソッドを `UpdateDatabase` メソッドの呼び出しに置き換えます。  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### ユーザーに対する選択肢の表示  
 上のコードにより `CreateMessage` プロシージャが呼び出され、ユーザーにエラー情報が表示されます。  このチュートリアルでは、メッセージ ボックスを使って、異なるバージョンのレコードをユーザーに表示します。ユーザーは、変更内容でレコードを上書きするか、編集をキャンセルするかを選択できます。  ユーザーがメッセージ ボックスのオプションを選択する \(ボタンをクリックする\) と、`ProcessDialogResult` メソッドに応答が渡されます。  
  
##### ユーザーに表示するメッセージを作成するには  
  
-   **コード エディター**に次のコードを追加して、メッセージを作成します。  このコードは、`UpdateDatabase` メソッドの下に入力します。  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### ユーザーの応答の処理  
 メッセージ ボックスへのユーザーの応答を処理するコードも必要です。  オプションは、データベースの現在のレコードを提案された変更内容で上書きするか、またはローカルの変更内容を破棄し、データベースの現在のレコードでデータ テーブルを更新するかのいずれかです。  ユーザーが yes を選択した場合、*preserveChanges* 引数が `true` に設定された <xref:System.Data.DataTable.Merge%2A> メソッドが呼び出されます。  この結果、レコードの元のバージョンがデータベースのレコードと一致するようになり、更新の試みは成功します。  
  
##### メッセージ ボックスからのユーザーの入力を処理するには  
  
-   前の手順で追加したコードの下に次のコードを追加します。  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## テスト  
 フォームをテストして、期待どおりに動作することを確認します。  同時実行違反をシミュレートするには、NorthwindDataSet にデータを読み込んだ後で、データベースのデータを変更する必要があります。  
  
#### フォームをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  フォームが表示されたら、実行を継続したまま Visual Studio IDE に切り替えます。  
  
3.  **\[表示\]** メニューの **\[サーバー エクスプローラー\]** をクリックします。  
  
4.  **サーバー エクスプローラー**で、アプリケーションで使用する接続を展開し、**\[テーブル\]** ノードを展開します。  
  
5.  **Customers** テーブルを右クリックし、**\[テーブル データの表示\]** をクリックします。  
  
6.  最初のレコード \(`ALFKI`\) で、`ContactName` を `Maria Anders2` に変更します。  
  
    > [!NOTE]
    >  別の行に移動し、変更をコミットします。  
  
7.  `ConcurrencyWalkthrough` の実行中のフォームに切り替えます。  
  
8.  フォームの最初のレコード \(`ALFKI`\) で、`ContactName` を `Maria Anders1` に変更します。  
  
9. **\[データの保存\]** をクリックします。  
  
     同時実行エラーが発生し、メッセージ ボックスが表示されます。  
  
10. **\[No\]** をクリックして更新をキャンセルし、データベースの現在の値でデータセットを更新するか、または **\[Yes\]** をクリックし、提案された値をデータベースに書き込みます。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)