---
title: "チュートリアル : ドキュメント レベルのプロジェクトでの単純データ バインド | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発], バインド (データを)"
  - "データ バインド [Visual Studio での Office 開発], ワークシートのセルをデータベース フィールドに"
  - "データベース フィールド [Visual Studio での Office 開発]"
  - "単純データ バインド [Visual Studio での Office 開発]"
  - "ワークシート [Visual Studio での Office 開発], バインディング (ワークシートのセルをデータベース フィールドに)"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# チュートリアル : ドキュメント レベルのプロジェクトでの単純データ バインド
  このチュートリアルでは、ドキュメント レベルのプロジェクトでのデータ バインディングの基本事項について説明します。  SQL Server データベース内の単一のデータ フィールドを Microsoft Office Excel 内の名前付き範囲にバインドする方法について説明します。  テーブル内のすべてのレコードをスクロールできるようにするコントロールを追加する方法も説明します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Excel プロジェクトのデータ ソースの作成  
  
-   ワークシートへのコントロールの追加  
  
-   データベース レコード間のスクロール  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
-   SQL Server データベースの読み込み\/書き込みアクセス許可  
  
## 新規プロジェクトの作成  
 この手順では、Excel ブックのプロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  Visual Basic または C\# を使用して、"**My Simple Data Binding**" という名前の Excel ブック プロジェクトを作成します。  **\[新規ドキュメントの作成\]** が選択されていることを確認します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 新しい Excel ブックが Visual Studio のデザイナーで開き、My Simple Data Binding プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
 **\[データ ソース\]** ウィンドウを使用して型指定されたデータセットをプロジェクトに追加します。  
  
#### データ ソースを作成するには  
  
1.  **\[データ ソース\]** のウィンドウが表示されない場合は、これを、**\[ビュー\]**、**\[その他のウィンドウ\]** を選択する、メニュー バーの **\[データ ソース\]** 表示されます。  
  
2.  **\[データ ソース構成ウィザード\]** を開始するには **\[新しいデータ ソースの追加\]** を選択します。  
  
3.  **\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  Northwind サンプル SQL Server データベースへのデータ接続を選択するか、または **\[新しい接続\]** をクリックして新しい接続を追加します。  
  
5.  接続を選択または作成した後、**\[次へ\]** をクリックします。  
  
6.  接続を保存するオプションがオンになっている場合はオフにし、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクト\]** ウィンドウの **\[テーブル\]** ノードを展開します。  
  
8.  **\[Customers\]** テーブルの横にあるチェック ボックスをオンにします。  
  
9. \[完了\] をクリックします。  
  
 **\[Customers\]** テーブルが **\[データ ソース\]** ウィンドウに追加されます。  さらに、**ソリューション エクスプローラー**に表示されるプロジェクトに、型指定されたデータセットも追加されます。  
  
## ワークシートへのコントロールの追加  
 このチュートリアルでは、2 つの名前付き範囲と 4 つのボタンが最初のワークシートに必要です。  最初に、2 つの名前付き範囲を **\[データ ソース\]** ウィンドウから追加して自動的にデータ ソースにバインドされるようにします。  次に、**ツールボックス**からボタンを追加します。  
  
#### 2 つの名前付き範囲を追加するには  
  
1.  **\[My Simple Data Binding.xlsx\]** ブックが Visual Studio のデザイナーで開いていると、表示 **\[Sheet1\]** ことを確認します。  
  
2.  **\[データ ソース\]** ウィンドウを開き、**\[Customers\]** ノードを展開します。  
  
3.  **\[CompanyName\]** 列を選択し、表示されるドロップダウン矢印をクリックします。  
  
4.  ドロップダウン リストの **NamedRange** を選択し、**CompanyName** 列をセル **A1** にドラッグします。  
  
     `companyNameNamedRange` という <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがセル **A1** に作成されます。  それと同時に、`customersBindingSource` という <xref:System.Windows.Forms.BindingSource>、テーブル アダプター、および <xref:System.Data.DataSet> インスタンスがプロジェクトに追加されます。  コントロールは <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれが <xref:System.Data.DataSet> インスタンスにバインドされます。  
  
5.  **\[データ ソース\]** ウィンドウの **\[CustomerID\]** 列を選択し、表示されるドロップダウン矢印をクリックします。  
  
6.  ドロップダウン リストの **\[NamedRange\]** を選択し、**\[CustomerID\]** 列をセル **B1** にドラッグします。  
  
7.  `customerIDNamedRange` という別の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがセル **B1** 内に作成され、<xref:System.Windows.Forms.BindingSource> にバインドされます。  
  
#### 4 つのボタンを追加するには  
  
1.  **ツールボックス**の **\[コモン コントロール\]** タブからワークシートのセル **A3** へ、<xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
     このボタンは `Button1` という名前になります。  
  
2.  残りの 3 つのボタンを次の順序でセルに追加し、ボタンがこのとおりの名前になるようにします。  
  
    |セル|\(Name\)|  
    |--------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 次の手順で、テキストをボタンに追加します。C\# ではイベント ハンドラーを追加します。  
  
## コントロールの初期化  
 ボタン テキストを設定し、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント中にイベント ハンドラーを追加します。  
  
#### コントロールを初期化するには  
  
1.  **ソリューション エクスプローラー**の **Sheet1.vb** または **Sheet1.cs** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  各ボタンにテキストを設定する次のコードを `Sheet1_Startup` メソッドに追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  C\# の場合のみ、ボタン クリック イベントのイベント ハンドラーを `Sheet1_Startup` メソッドに追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 <xref:System.Windows.Forms.Control.Click> ボタンのイベントを処理するコードを追加し、ユーザーがレコード間を移動できるようにします。  
  
## レコード間をスクロールするためのコードの追加  
 レコード間を移動するためのコードを各ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに追加します。  
  
#### 最初のレコードに移動するには  
  
1.  `Button1` ボタンの <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを追加し、最初のレコードに移動するための次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### 後方のレコードに移動するには  
  
1.  `Button2` ボタンの <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを追加し、位置を 1 つ後方に移動するための次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### 次のレコードに移動するには  
  
1.  `Button3` ボタンの <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを追加し、位置を 1 つ前方に移動するための次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### 最後のレコードに移動するには  
  
1.  `Button4` ボタンの <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを追加し、最後のレコードに移動するための次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## アプリケーションのテスト  
 ブックをテストして、データベース内のレコード間を移動できることを確認できます。  
  
#### ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  最初のレコードがセル **A1** とセル **B1** に表示されることを確認します。  
  
3.  **\[\>\]** \(`Button3`\) ボタンをクリックし、次のレコードがセル **A1** とセル **B1** に表示されることを確認します。  
  
4.  他のスクロール ボタンをクリックして、レコードが適切に変わることを確認します。  
  
## 次の手順  
 このチュートリアルでは、名前付き範囲をデータベース内のフィールドにバインドする際の基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   データをキャッシュしてオフラインで使用できるようにします。  詳細については、「[方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)」を参照してください。  
  
-   セルを 1 つのフィールドではなくテーブル内の複数の列にバインドします。  詳細については、「[チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインド](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.BindingNavigator> コントロールを使用してレコード間をスクロールします。  詳細については、「[方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインド](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  