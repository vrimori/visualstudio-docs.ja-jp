---
title: "方法 : サンプル データベースをインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Adventure Works サンプル データベース"
  - "データ [Visual Studio], サンプル データベース"
  - "Northwind サンプル データベース"
  - "サンプル データベース, Adventure Works"
  - "サンプル データベース, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : サンプル データベースをインストールする
多くのデータ例で、サンプル データベース Northwind、Pubs、および AdventureWorks への接続が必要になります。  これらのデータベースには、次の手順に従ってインストールし、接続できます。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## データベースのインストール  
 多くのデータ サンプルでは、Web サイトからダウンロードできるサンプル データベースを使用できることが必要です。  サンプル データベースには、AdventureWorks、Northwind、および Pubs データベースが含まれています。  
  
#### SQL Server 用の Northwind サンプル データベースと Pubs サンプル データベースをインストールするには  
  
1.  [Northwind および Pubs サンプル データベース](http://go.microsoft.com/fwlink?linkid=64296)の Web サイトにアクセスします。  
  
2.  インストーラーをダウンロードして実行します。  
  
     インストーラーにより、コンピューターのルート フォルダーに、**SQL Server 2000 Sample Databases** フォルダーが追加されます   \(**C:\\SQL Server 2000 Sample Databases** など\)。  
  
3.  必要なデータベース \(Northwind または Pubs\) に対応する SQL スクリプトを探します。  
  
    > [!WARNING]
    >  .MDF データベース ファイルは SQL Server の現在のバージョンで使用できる形式に簡単に変換できないため、スクリプトを使用してデータベースを作成することをお勧めします。  
  
4.  **サーバー エクスプローラー**で、データベースをインストールする SQL Server インスタンスへの接続を作成します。  使用する特定の SQL Server が存在しない場合は、Visual Studio と共に自動的にインストールされるデータベースを使用できます。  これを行うには、サーバー名として `(localdb)\v11.0` を指定します。  
  
     接続を作成するには、次の手順に従います。  
  
    ###### SQL Server インスタンスへの接続を作成するには  
  
    1.  **サーバー エクスプローラー**で、**\[データ接続\]** ノードのショートカット メニューを開いて、**\[接続の追加\]** をクリックします。  
  
         **\[接続の追加\]** ダイアログ ボックスが表示されます。  
  
    2.  Northwind データベースまたは Pubs データベースを作成する SQL Server の名前を指定するか、「\(localdb\)\\v11.0」と入力します。  
  
    3.  **\[データベース名の選択または入力\]** で、一覧からデータベース \(tempdb など\) を選択します。  
  
    4.  **\[テスト接続\]** をクリックしてすべての動作が正常であることを確認し、**\[OK\]** をクリックします。  
  
         新しい接続ノードが**サーバー エクスプローラー**に表示されます。  
  
5.  使用するサーバーに対応する接続ノードのショートカット メニューで、**\[新しいクエリ\]** をクリックします。  
  
     エディター ウィンドウが開き、空の .sql スクリプト ファイルが表示されます。  
  
6.  instnwnd.sql または instpubs.sql の内容をエディター ウィンドウに貼り付けます。  
  
7.  \[クエリの実行\] ボタン \(クエリ ウィンドウの右上にある、塗りつぶされていない緑色の三角のアイコン\) を選択します。  
  
     クエリが成功すると、**"コマンドは正常に完了しました"** というメッセージが表示されます。  これは、Northwind または pubs データベースが作成されたことを意味します。  
  
     次に、サンプル データベースに接続を追加する必要があります。  **サーバー エクスプローラー**で、**\[データ接続\]** ノードのショートカット メニューを開いて、**\[接続の追加\]** を選択します。  
  
8.  以前選択したものと同じデータベース サーバーを選択しますが、今回は \[選択\] で、またはデータベース名を入力して、Northwind または pubs データベースを選択して、**\[OK\]** を選択します。  
  
     サンプル データベースの \[データ接続\] の下に、新しいノードが表示されます。  
  
9. エディター ウィンドウを閉じ、クエリ ファイルを保存しないことを確認します。  データベースの作成後は、データベース作成スクリプトを保存する必要はありません。  
  
#### AdventureWorks サンプル データベースをインストールするには  
  
-   AdventureWorks サンプル データベースを [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)からダウンロードします。  
  
#### Microsoft Access 用の Northwind サンプル データベースをインストールするには  
  
1.  Microsoft Access 2010 以降で、Northwind 用のオンライン テンプレートを検索し、**デスクトップ Northwind 2007 サンプル データベース**を選択します。  
  
2.  Microsoft Access で、データベース ファイルを Northwind.accdb として保存します。  
  
 Access データベースの新しい拡張子は .accdb です。  「[Access 2010 を使用したデータ プログラミング](http://msdn.microsoft.com/library/office/ff965871.aspx)」を参照してください。  Access を使用して Northwind データベースに接続するには、「[方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)」を参照してください。  
  
## .NET Framework セキュリティ  
 サンプル データベースは例示のみを目的としており、必ずしもセキュリティに関するベスト プラクティスを示しているとは限りません。  
  
## 参照  
 [SQL Server とそのコンポーネントのバージョンとエディションを確認する方法](http://support.microsoft.com/kb/321185)   
 [チュートリアル: Visual Studio でのローカル データベース ファイルの作成](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)