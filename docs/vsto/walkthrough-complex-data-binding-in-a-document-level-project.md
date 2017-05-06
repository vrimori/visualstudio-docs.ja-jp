---
title: "チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインド"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "複合データ [Visual Studio での Office 開発]"
  - "データ [Visual Studio での Office 開発], バインド (データを)"
  - "データ バインド [Visual Studio での Office 開発], 複数列"
  - "複数列のデータ バインド [Visual Studio での Office 開発]"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインド
  このチュートリアルでは、ドキュメント レベルのプロジェクトでの複合データ バインディングの基本事項について説明します。  Microsoft Office Excel ワークシートの複数のセルを Northwind SQL Server データベースのフィールドにバインドできます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ブック プロジェクトにデータ ソースを追加します。  
  
-   ワークシートにデータ バインド コントロールを追加します。  
  
-   データの変更内容をデータベースに保存します。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
-   SQL Server データベースの読み込み\/書き込みアクセス許可  
  
## 新規プロジェクトの作成  
 最初に、Excel ブック プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  **My Complex Data Binding** という名前の Excel ブック プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Excel ブックが Visual Studio のデザイナーで開き、My Complex Data Binding プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
 **\[データ ソース\]** ウィンドウを使用して型指定されたデータセットをプロジェクトに追加します。  
  
#### データ ソースを作成するには  
  
1.  **\[データ ソース\]** のウィンドウが表示されない場合は、これを、**\[ビュー\]**、**\[その他のウィンドウ\]** を選択する、メニュー バーの **\[データ ソース\]** 表示されます。  
  
2.  **\[データ ソース構成ウィザード\]** を開始するには **\[新しいデータ ソースの追加\]** を選択します。  
  
3.  **\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  SQL Server Northwind サンプル データベースへのデータ接続を選択するか、または **\[新しい接続\]** をクリックして新しい接続を追加します。  
  
5.  接続を選択または作成した後、**\[次へ\]** をクリックします。  
  
6.  接続を保存するオプションがオンになっている場合はオフにし、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクト\]** ウィンドウの **\[テーブル\]** ノードを展開します。  
  
8.  **\[Employees\]** テーブルの横のチェック ボックスをオンにします。  
  
9. \[完了\] をクリックします。  
  
 **\[データ ソース\]** ウィンドウに **\[Employees\]** テーブルが追加されます。  さらに、**ソリューション エクスプローラー**に表示されるプロジェクトに、型指定されたデータセットも追加されます。  
  
## ワークシートへのコントロールの追加  
 ブックを開くと、ワークシートに **Employees** テーブルが表示されます。  ユーザーは、データに変更を加え、ボタンをクリックして変更内容をデータベースに保存できます。  
  
 テーブルに対してワークシートを自動的にバインドするには、**\[データ ソース\]** ウィンドウからワークシートに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加します。  変更を保存するオプションをユーザーが選択できるようにするには、**ツールボックス**から <xref:System.Windows.Forms.Button> コントロールを追加します。  
  
#### リスト オブジェクトを追加するには  
  
1.  **\[My Complex Data Binding.xlsx\]** ブックが Visual Studio のデザイナーで開いていると、表示 **\[Sheet1\]** ことを確認します。  
  
2.  **\[データ ソース\]** ウィンドウを開き、**\[Employees\]** ノードを選択します。  
  
3.  表示されるドロップダウン矢印をクリックします。  
  
4.  ドロップダウン リストで **\[ListObject\]** を選択します。  
  
5.  **Employees** テーブルをセル **A6** にドラッグします。  
  
     `EmployeesListObject` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがセル **A6** に作成されます。  同時に、`EmployeesBindingSource` という名前の <xref:System.Windows.Forms.BindingSource>、テーブル アダプター、および <xref:System.Data.DataSet> のインスタンスがプロジェクトに追加されます。  コントロールは <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれが <xref:System.Data.DataSet> インスタンスにバインドされます。  
  
#### ボタンを追加するには  
  
1.  **ツールボックス**の **\[コモン コントロール\]** タブからワークシートのセル **A4** へ、<xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
 次の手順では、ワークシートを開くときにボタンにテキストを追加します。  
  
## コントロールの初期化  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント ハンドラーで、ボタンにテキストを追加します。  
  
#### コントロールを初期化するには  
  
1.  **ソリューション エクスプローラー**の **Sheet1.vb** または **Sheet1.cs** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  `Sheet1_Startup` メソッドに次のコードを追加し、`button` のテキストを設定します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  C\# の場合のみ、<xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを `Sheet1_Startup` メソッドに追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 ボタンの <xref:System.Windows.Forms.Control.Click> イベントを処理するコードを追加します。  
  
## データベースへの変更の保存  
 データに加えられた変更は、明示的にデータベースに保存されない限り、ローカル データセット内でのみ存在します。  
  
#### データベースに変更を保存するには  
  
1.  `button` の <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを追加し、次のコードを追加して、データセット内で行われたすべての変更をデータベースにコミットします。  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## アプリケーションのテスト  
 ブックをテストして、データが期待どおりに表示され、リスト オブジェクト内のデータを操作できることを確認します。  
  
#### データ バインディングをテストするには  
  
-   F5 キーを押します。  
  
     ブックを開いたときに、**Employees** テーブルのデータがリスト オブジェクトに設定されていることを確認します。  
  
#### データを変更するには  
  
1.  **Davolio** という名前が含まれているセル **B7** をクリックします。  
  
2.  「Anderson」という名前を入力し、Enter キーを押します。  
  
#### 列ヘッダーを変更するには  
  
1.  **LastName** という列ヘッダーを含むセルをクリックします。  
  
2.  「Last Name」\(2 つの単語の間には空白を含む\) を入力し、Enter キーを押します。  
  
#### データを保存するには  
  
1.  ワークシートの **\[\<ファイル名\> の保存\]** をクリックします。  
  
2.  Excel を終了します。  変更の保存を確認するメッセージに対して、**\[いいえ\]** をクリックします。  
  
3.  F5 キーを押してプロジェクトを再び実行します。  
  
     リスト オブジェクトには、**Employees** テーブルのデータが設定されます。  
  
4.  セル **B7** 内の名前は Anderson であることに注意してください。これは、変更してデータベースに保存したデータです。  列ヘッダーの **LastName** は、空白を含まない元の形式に戻っています。これは、列ヘッダーはデータベースにバインドされておらず、ワークシートへの変更を保存しなかったためです。  
  
#### 新規行を追加するには  
  
1.  リスト オブジェクト内のセルを選択します。  
  
     リストの下部に新規行が表示され、新規行の先頭のセルにはアスタリスク \(**\***\) が表示されます。  
  
2.  空の行に次の情報を追加します。  
  
    |EmployeeID|LastName|FirstName|Title|  
    |----------------|--------------|---------------|-----------|  
    |10|Ito|Shu|Sales Manager|  
  
#### 行を削除するには  
  
-   ワークシートの左端にある番号 16 \(行 16\) をクリックして、**\[削除\]** をクリックします。  
  
#### リスト内の行を並べ替えるには  
  
1.  リスト内のセルを選択します。  
  
     各列ヘッダーに矢印ボタンが表示されます。  
  
2.  **\[Last Name\]** という列ヘッダーの矢印ボタンをクリックします。  
  
3.  **\[昇順で並べ替え\]** をクリックします。  
  
     姓のアルファベット順に行が並べ替えられます。  
  
#### 情報をフィルター処理するには  
  
1.  リスト内のセルを選択します。  
  
2.  **\[Title\]** という列ヘッダーの矢印ボタンをクリックします。  
  
3.  **\[Sales Representative\]** をクリックします。  
  
     **\[Title\]** 列が **\[Sales Representative\]** の行のみ表示されます。  
  
4.  **\[Title\]** という列ヘッダーの矢印ボタンを再びクリックします。  
  
5.  **\[\(すべて\)\]** をクリックします。  
  
     フィルターが削除され、すべての行が表示されます。  
  
## 次の手順  
 このチュートリアルでは、データベース内のテーブルをリスト オブジェクトにバインドする際の基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   データをキャッシュしてオフラインで使用できるようにします。  詳細については、「[方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)」を参照してください。  
  
-   ソリューションの配置。  詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
-   フィールドとテーブル間のマスター\/詳細リレーションシップの作成。  詳細については、「[チュートリアル : キャッシュされたデータセットを使用したマスター&#47;詳細関係の作成](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [チュートリアル : ドキュメント レベルのプロジェクトでの単純データ バインド](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  