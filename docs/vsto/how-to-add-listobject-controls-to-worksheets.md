---
title: "方法 : ワークシートに ListObject コントロールを追加する"
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
  - "ListObject コントロール、追加 (ワークシートに)"
  - "コントロール [Visual Studio での Office 開発]、追加 (ワークシートに)"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 方法 : ワークシートに ListObject コントロールを追加する
  ドキュメント レベルのプロジェクトでは、デザイン時および実行時に、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを Microsoft Office Excel ワークシートに追加できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドイン プロジェクトでも、実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時の ListObject コントロールの追加](#designtime)  
  
-   [ドキュメント レベルのプロジェクトで、ListObject コントロールを実行時に追加する](#runtimedoclevel)  
  
-   [VSTO アドイン プロジェクトで、ListObject コントロールを実行時に追加する](#runtimeaddin)  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールの詳細については、「[ListObject コントロール](../vsto/listobject-control.md)」を参照してください。  
  
##  <a name="designtime"></a> デザイン時の ListObject コントロールの追加  
 デザイン時にドキュメント レベルのプロジェクトのワークシートに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加する方法として、Excel から行う方法、Visual Studio の**ツールボックス**から行う方法、および **\[データ ソース\]** ウィンドウから行う方法があります。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Excel のリボンを使用するには  
  
1.  **\[挿入\]** タブの **\[テーブル\]** グループで、**\[テーブル\]** をクリックします。  
  
2.  リストに含める 1 つ以上のセルを選択し、**\[OK\]** をクリックします。  
  
#### ツールボックスを使用するには  
  
1.  **ツールボックス**の **\[Excel コントロール\]** タブからワークシートまで <xref:Microsoft.Office.Tools.Excel.ListObject> をドラッグします。  
  
     **\[ListObject コントロールの追加\]** ダイアログ ボックスが表示されます。  
  
2.  リストに含める 1 つ以上のセルを選択し、**\[OK\]** をクリックします。  
  
     名前を既定のままにしない場合は、**\[プロパティ\]** ウィンドウで変更します。  
  
#### \[データ ソース\] ウィンドウを使用するには  
  
1.  **\[データ ソース\]** ウィンドウを開いて、プロジェクトのデータ ソースを作成します。 詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
2.  **\[データ ソース\]** ウィンドウからワークシートまでテーブルをドラッグします。  
  
     データがバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがワークシートに追加されます。 詳細については、「[データ連結と Windows フォーム](../Topic/Data%20Binding%20and%20Windows%20Forms.md)」を参照してください。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベルのプロジェクトで、ListObject コントロールを実行時に追加する  
 実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを動的に追加できます。 この方法を使用すると、イベントに応答してホスト コントロールを作成できます。 動的に作成されたリスト オブジェクトは、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
#### プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント ハンドラーに以下のコードを挿入して、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4** に追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトで、ListObject コントロールを実行時に追加する  
 プログラムによって <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 動的に作成されたリスト オブジェクトは、ワークシートを保存して閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
#### プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4** に追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [方法 : ListObject コントロールのサイズを変更する](../vsto/how-to-resize-listobject-controls.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  