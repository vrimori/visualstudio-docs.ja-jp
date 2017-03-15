---
title: "チュートリアル: Visual Studio でのローカル データベース ファイルの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "データ [Visual Studio], ローカル データ"
  - "データ [Visual Studio], チュートリアル"
  - "データベース ファイル, 作成"
  - "データベース, 作成"
  - "ローカル データ"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Express"
  - "SQLEXPRESS"
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 49
caps.handback.revision: 44
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル: Visual Studio でのローカル データベース ファイルの作成
SQL Server Express LocalDB にローカル データベース ファイルを作成して更新するために、Visual Studio を使用して、テーブルの追加、列の定義などの基本的なタスクを実行できます。「[ローカル データの概要](../data-tools/local-data-overview.md)」で説明します。  このチュートリアルを終了すると、ローカル データベースを使用してさらに高度な機能を使用できるようになり、こうした機能を必要とする他のチュートリアルへの準備となります。  
  
 SQL Server Management Studio または Transact\-SQL を使用してデータベースを作成する方法の詳細については、「[Create a Database](http://msdn.microsoft.com/ja-jp/4c4beea2-6cbc-4352-9db6-49ea8130bb64)」を参照してください。  
  
 このチュートリアルには次のタスクがあります。  
  
-   [プロジェクトとローカル データベース ファイルの作成](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)。  
  
-   [テーブル、列、主キー、外部キーの作成](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)。  
  
-   [テーブルへのデータの読み込み](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、[!INCLUDE[vs_dev12_expwin](../data-tools/includes/vs_dev12_expwin_md.md)]、Visual Studio Professional 2013、Visual Studio Premium 2013、または Visual Studio Ultimate 2013 をインストールする必要があります。  Visual Studio のこれらのバージョンには、SQL Server Data Tools が含まれています。  
  
##  <a name="BKMK_CreateNewSQLDB"></a> プロジェクトとローカル データベース ファイルの作成  
  
#### プロジェクトとローカル データベース ファイルを作成するには  
  
1.  `SampleDatabaseWalkthrough` という名前の Windows フォーム プロジェクトを作成します。  
  
     「[ソリューションとプロジェクトの作成](../ide/creating-solutions-and-projects.md)」を参照してください。  
  
2.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示され、Windows フォーム プロジェクトに適切な項目を追加できます。  
  
3.  項目テンプレートの一覧で、**サービス ベースのデータベース**が表示されるまでスクロールし、これを選択します。  
  
     ![&#91;アイテム テンプレート&#93; ダイアログ ボックス](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4.  このデータベースに「SampleDatabase」という名前を付け、**\[追加\]** をクリックします。  
  
5.  **\[データ ソース\]** ウィンドウが開かない場合は、Shift \+ Alt \+ D キーを押すか、メニュー バーで **\[表示\]**、**\[その他のウィンドウ\]**、\[データ ソースの表示\] の順にクリックして開きます。  
  
6.  \[データ ソース\] ウィンドウで **\[新しいデータ ソースの追加\]** リンクをクリックします。  
  
7.  **データ ソース構成ウィザード**で、**\[次へ\]** ボタンを 4 回クリックして既定の設定を使用し、次に **\[完了\]** ボタンをクリックします。  
  
 データベースのプロパティ ウィンドウを開くと、その接続文字列と、プライマリ .mdf ファイルの位置を確認できます。  
  
-   Visual Studio Express で、データベース エクスプローラーのウィンドウがまだ開いていない場合は、**\[表示\]**、**\[その他のウィンドウ\]**、**\[データベース エクスプローラー\]** をクリックします。  **\[データ接続\]** ノードを展開し、SampleDatabase.mdf のショートカット メニューを開いた後、**\[プロパティ\]** をクリックしてプロパティ ウィンドウを開きます。  
  
-   Visual Studio の他のバージョンで、サーバー エクスプローラーのウィンドウがまだ開いていない場合は、**\[表示\]**、**\[サーバー エクスプローラー\]** をクリックします。  **\[データ接続\]** ノードを展開し、SampleDatabase.mdf のショートカット メニューを開いた後、**\[プロパティ\]** をクリックしてプロパティ ウィンドウを開きます。  
  
##  <a name="BKMK_CreateNewTbls"></a> テーブル、列、主キー、外部キーの作成  
 このセクションでは、いくつかのテーブルと各テーブルの主キー、およびサンプル データの行を作成します。  次のチュートリアルでは、この情報がアプリケーションでどのように表示されるかを理解することができます。  また外部キーを作成して、1 つのテーブルのレコードが他のテーブルのレコードに対応する方法を指定できます。  
  
#### Customers テーブルを作成するには  
  
1.  **\[サーバー エクスプローラー\]** または **\[データベース エクスプローラー\]** で、**\[データ接続\]** のノードを展開し、**SampleDatabase.mdf** ノードを展開します。  
  
     使用しているバージョンの Visual Studio のエクスプローラーが開いていない場合は、メニュー バーで、**\[表示\]**、**\[サーバー エクスプローラー\]** の順に、または **\[表示\]**、**\[その他のウィンドウ\]**、**\[データベース エクスプローラー\]** の順にクリックします。  
  
2.  **\[テーブル\]** のショートカット メニューを開き、**\[新しいテーブルの追加\]** をクリックします。  
  
     **\[テーブル デザイナー\]** は、作成しているテーブルの 1 つの列を表す、1 つの既定の行のグリッドを開いて表示します。  行をグリッドに追加することによって、テーブルに列を追加します。  
  
3.  グリッドで、次のエントリのそれぞれに行を追加します。  
  
    |列名|\[データ型\]|Null を許容|  
    |--------|--------------|--------------|  
    |`CustomerID`|`nchar(5)`|false \(オフ\)|  
    |`CompanyName`|`nvarchar(40)`|false \(オフ\)|  
    |`ContactName`|`nvarchar (30)`|true \(オン\)|  
    |`Phone`|`nvarchar (24)`|true \(オン\)|  
  
4.  `CustomerID` の行でショートカット メニューを開き、**\[主キーの設定\]** をクリックします。  
  
5.  既定の行のショートカット メニューを開き、**\[削除\]** をクリックします。  
  
6.  スクリプト ペインの最初の行の次のサンプルのように更新して、Customers \(顧客\) をテーブルと名前を付けます:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
7.  次の図に示すように、テーブル デザイナーの左上にある **\[更新\]** をクリックします。  
  
     ![テーブル デザイナーの &#91;更新&#93; ボタン](../data-tools/media/updatelocaldb.png "UpdateLocalDB")  
  
8.  **\[データベース更新のプレビュー\]** ダイアログ ボックスで、**\[データベースの更新\]** をクリックします。  
  
     変更はローカル データベース ファイルに保存されます。  
  
#### Orders テーブルを作成するには  
  
1.  別のテーブルを追加し、次の表の各エントリの行を追加します。  
  
    |列名|データ型|Null を許容|  
    |--------|----------|--------------|  
    |`OrderID`|`int`|false \(オフ\)|  
    |`CustomerID`|`nchar(5)`|false \(オフ\)|  
    |`OrderDate`|`datetime`|true \(オン\)|  
    |`OrderQuantity`|`int`|true \(オン\)|  
  
2.  **\[OrderID\]** を主キーとして設定した後、既定の行を削除します。  
  
3.  スクリプト ペインの最初の行の次のサンプルのように更新して、Orders \(注文\) をテーブルと名前を付けます:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  テーブル デザイナーの左上にある **\[更新\]** をクリックします。  
  
5.  **\[データベース更新のプレビュー\]** ダイアログ ボックスで、**\[データベースの更新\]** をクリックします。  
  
     変更はローカル データベース ファイルに保存されます。  
  
#### 外部キーを作成するには  
  
1.  次の図に示すように、グリッドの右側のコンテキスト ペインで、**\[外部キー\]** ショートカット メニューを開き、**\[新しい外部キーを追加\]** をクリックします。  
  
     ![テーブル デザイナーでの外部キーの追加](../data-tools/media/foreignkey.png "ForeignKey")  
  
2.  表示されるテキスト ボックスで、**ToTable** を `Customers` に置換します。  
  
3.  スクリプト ペインで、次のサンプルのように最後の行を更新します:  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  テーブル デザイナーの左上にある **\[更新\]** をクリックします。  
  
5.  **\[データベース更新のプレビュー\]** ダイアログ ボックスで、**\[データベースの更新\]** をクリックします。  
  
     変更はローカル データベース ファイルに保存されます。  
  
##  <a name="BKMK_Populating"></a> テーブルへのデータの読み込み  
  
#### テーブルにデータを読み込むには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、サンプル データベースのノードを展開します。  
  
2.  \[テーブル\] ノードのショートカット メニューを開き、**\[最新の情報に更新\]** をクリックし、次に \[テーブル\] ノードを展開します。  
  
3.  Customers テーブルのショートカット メニューを開き、**\[テーブル データの表示\]** をクリックします。  
  
4.  最低 3 人の Customer \(顧客\) に任意のデータを追加します。  
  
     顧客 ID には任意の 5 文字を指定できます。この手順では、後で使用するために、少なくとも 1 つを選択します。  
  
5.  Orders テーブルのショートカット メニューを開き、**\[テーブル データの表示\]** をクリックします。  
  
6.  最低 3 件の注文データを追加します。  
  
    > [!IMPORTANT]
    >  すべての注文 ID および注文数量が整数であり、各顧客 ID が、Customers テーブルの CustomerID 列で指定した値と一致することを確認します。  
  
7.  メニュー バーで、**\[ファイル\]**、**\[すべてを保存\]** の順に選択します。  
  
8.  メニュー バーで **\[ファイル\]**、**\[ソリューションを閉じる\]** の順に選択します。  
  
    > [!NOTE]
    >  ベスト プラクティスとして、データベースをコピーし、他の場所にそのコピーを貼り付ける、またはコピーに異なる名前を付けることによって、作成したデータベースのバックアップを実行します。  
  
## 次の手順  
 これで、ローカル データベース ファイルにサンプル データが追加されました。データベースのタスクを紹介した他のチュートリアルに加えて、[チュートリアル: ローカル データベース ファイル内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md) も完了しました。  
  
## 参照  
 [方法 : プロジェクトでローカル データ ファイルを管理する](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [ローカル データの概要](../data-tools/local-data-overview.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)