---
title: "チュートリアル : 実行時における VSTO アドイン プロジェクトのワークシートへのコントロールの追加 | Microsoft Docs"
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
  - "アドイン [Visual Studio での Office 開発], 追加 (コントロールを)"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発], 追加 (コントロールを)"
  - "コントロール [Visual Studio での Office 開発], 追加 (実行時にワークシートに)"
  - "ワークシート, 追加 (実行時にコントロールを)"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル : 実行時における VSTO アドイン プロジェクトのワークシートへのコントロールの追加
  Excel VSTO アドインを使用して、任意の開いているワークシートにコントロールを追加できます。  このチュートリアルでは、リボンを使用してユーザーがワークシートに <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange>、および <xref:Microsoft.Office.Tools.Excel.ListObject> を追加できるようにする方法を説明します。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」をご覧ください。  
  
 **対象:** このトピックの情報は、Excel の VSTO アドインのプロジェクトに適用されます。  詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ワークシートにコントロールを追加するためのユーザー インターフェイス \(UI\) を提供する。  
  
-   ワークシートにコントロールを追加する。  
  
-   ワークシートからコントロールを削除する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## 新しい Excel VSTO アドイン プロジェクトの作成  
 まず、Excel VSTO アドイン プロジェクトを作成します。  
  
#### 新しい Excel VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で、ExcelDynamicControls という名前の Excel VSTO アドイン プロジェクトを作成します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
2.  **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** アセンブリへの参照を追加します。  この参照は、このチュートリアルの後半で Windows フォーム コントロールをワークシートにプログラムを使用して追加するのに必要です。  
  
## ワークシートにコントロールを追加するための UI の提供  
 Excel のリボンにカスタム タブを追加します。  ユーザーはタブにあるチェック ボックスをオンにして、ワークシートにコントロールを追加できます。  
  
#### ワークシートにコントロールを追加するための UI を提供するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[リボン \(ビジュアル デザイナー\)\]** を選択し、**\[追加\]** をクリックします。  
  
     リボン デザイナーで **Ribbon1.cs** または **Ribbon1.vb** という名前のファイルが開き、既定のタブとグループが表示されます。  
  
3.  **ツールボックス**の **\[Office リボン コントロール\]** タブから、CheckBox コントロールを **group1** にドラッグします。  
  
4.  **\[CheckBox1\]** をクリックしてオンにします。  
  
5.  **\[プロパティ\]** ウィンドウで、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|ボタン|  
    |**ラベル**|ボタン|  
  
6.  **group1** に 2 つ目のチェック ボックスを追加し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|NamedRange|  
    |**ラベル**|NamedRange|  
  
7.  **group1** に 3 つ目のチェック ボックスを追加し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|ListObject|  
    |**ラベル**|ListObject|  
  
## ワークシートへのコントロールの追加  
 マネージ コントロールは、ホスト項目に対してのみ追加できます。これは、コンテナーとして機能します。  VSTO アドイン プロジェクトは任意の開いているブックを操作するため、VSTO アドインはワークシートをホスト項目に変換するか、または既存のホスト項目を取得してから、コントロールを追加します。  開いているワークシートに基づく <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を生成するように、各コントロールのクリック イベント ハンドラーにコードを追加します。  次に、ワークシートの現在選択されている位置に <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange>、および <xref:Microsoft.Office.Tools.Excel.ListObject> を追加します。  
  
#### ワークシートにコントロールを追加するには  
  
1.  リボン デザイナーで **\[Button\]** をダブルクリックします。  
  
     **\[Button\]** チェック ボックスの <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> イベント ハンドラーがコード エディターで開きます。  
  
2.  `Button_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     このコードでは、`GetVstoObject` メソッドを使用してブックの最初のワークシートを表すホスト項目を取得し、現在選択されているセルに <xref:Microsoft.Office.Tools.Excel.Controls.Button> コントロールを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  **ソリューション エクスプ ローラー**で、Ribbon1.cs または Ribbon1.vb を選択します。  
  
4.  **\[表示\]** メニューの **\[デザイナー\]** をクリックします。  
  
5.  リボン デザイナーで **\[NamedRange\]** をダブルクリックします。  
  
6.  `NamedRange_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     このコードでは、`GetVstoObject` メソッドを使用してブックの最初のワークシートを表すホスト項目を取得し、現在選択されている \(1 つまたは複数の\) セルの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを定義します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  リボン デザイナーで **\[ListObject\]** をダブルクリックします。  
  
8.  `ListObject_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     このコードでは、`GetVstoObject` メソッドを使用してブックの最初のワークシートを表すホスト項目を取得し、現在選択されている \(1 つまたは複数の\) セルの <xref:Microsoft.Office.Tools.Excel.ListObject> を定義します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. リボン コード ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## ワークシートからコントロールを削除する。  
 ワークシートが保存されて閉じられるとき、コントロールは保持されません。  ワークシートを保存する前に、生成されたすべての Windows フォーム コントロールをプログラムを使用して削除する必要があります。そうしないと、ワークシートを再び開いたときに、コントロールのアウトラインのみが表示されます。  生成されたホスト項目のコントロール コレクションから Windows フォーム コントロールを削除するコードを <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> イベントに追加します。  詳細については、「[Office ドキュメントでのダイナミック コントロールの永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)」をご覧ください。  
  
#### ワークシートからコントロールを削除するには  
  
1.  **ソリューション エクスプ ローラー**で、ThisAddIn.cs または ThisAddIn.vb を選択します。  
  
2.  **\[表示\]** メニューの **\[コード\]** をクリックします。  
  
3.  次のメソッドを ThisAddIn クラスに追加します。  このコードはブックの最初のワークシートを取得し、`HasVstoObject` メソッドを使用して、ワークシートにワークシート オブジェクトが生成されているかどうかを確認します。  生成されたワークシート オブジェクトにコントロールがある場合、コードはそのワークシート オブジェクトを取得し、コントロール コレクションを反復処理してコントロールを削除します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  C\# では、<xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> イベントのイベント ハンドラーを作成する必要があります。  このコードを `ThisAddIn_Startup` メソッドに配置できます。  イベント ハンドラーの作成に関する詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」をご覧ください。  `ThisAddIn_Startup` メソッドを次のコードに置き換えます。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## ソリューションのテスト  
 リボンのカスタム タブからコントロールを選択し、ワークシートに追加します。  ワークシートを保存すると、これらのコントロールは削除されます。  
  
#### ソリューションをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  Sheet1 で任意のセルを選択します。  
  
3.  **\[アドイン\]** タブをクリックします。  
  
4.  **\[Group1\]** グループで、**\[Button\]** をクリックします。  
  
     選択したセルにボタンが表示されます。  
  
5.  Sheet1 で別のセルを選択します。  
  
6.  **\[Group1\]** グループで、**\[NamedRange\]** をクリックします。  
  
     選択したセルに名前付き範囲が定義されます。  
  
7.  Sheet1 で一連のセルを選択します。  
  
8.  **\[Group1\]** グループで、**\[ListObject\]** をクリックします。  
  
     選択したセルにリスト オブジェクトが追加されます。  
  
9. ワークシートを保存します。  
  
     Sheet1 に追加したコントロールは表示されなくなります。  
  
## 次の手順  
 Excel VSTO アドイン プロジェクトのコントロールの詳細については、以下のトピックをご覧ください。  
  
-   ワークシートにコントロールを保存する方法の詳細については、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」にある、Excel VSTO アドイン ダイナミック コントロールのサンプルをご覧ください。  
  
## 参照  
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ListObject コントロール](../vsto/listobject-control.md)  
  
  