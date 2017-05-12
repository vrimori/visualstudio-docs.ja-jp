---
title: "方法 : ワークシートに NamedRange コントロールを追加する"
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
  - "範囲、追加 (ワークシートに)"
  - "NamedRange コントロール、追加 (ワークシートに)"
  - "コントロール [Visual Studio での Office 開発]、追加 (ワークシートに)"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 方法 : ワークシートに NamedRange コントロールを追加する
  ドキュメント レベルのプロジェクトでは、デザイン時および実行時に、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを Microsoft Office Excel ワークシートに追加できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドイン プロジェクトでも、実行時に <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に NamedRange コントロールを追加する](#designtime)  
  
-   [実行時にドキュメント レベルのプロジェクトの NamedRange コントロールを追加する](#runtimedoclevel)  
  
-   [実行時に VSTO アドイン プロジェクトの NamedRange コントロールを追加する](#runtimeaddin)  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロール細について詳しくは、「[NamedRange コントロール](../vsto/namedrange-control.md)」をご覧ください。  
  
##  <a name="designtime"></a> デザイン時に NamedRange コントロールを追加する  
 デザイン時にドキュメント レベルのプロジェクトのワークシートに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加する方法として、Excel から行う方法、Visual Studio の**ツールボックス**から行う方法、**\[データ ソース\]** ウィンドウから行う方法があります。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Excel で \[名前ボックス\] を使用してワークシートに NamedRange コントロールを追加するには  
  
1.  名前付き範囲に含める 1 つ以上のセルを選びます。  
  
2.  **\[名前ボックス\]** に範囲の名前を入力し、Enter キーを押します。  
  
     **\[名前ボックス\]** は、数式バーの横、ワークシートの列 **A** の真上にあります。  
  
#### ツールボックスを使用してワークシートに NamedRange コントロールを追加するには  
  
1.  **ツールボックス**を開き、**\[Excel コントロール\]** タブをクリックします。  
  
2.  <xref:Microsoft.Office.Tools.Excel.NamedRange> をクリックし、ワークシートにドラッグします。  
  
     **\[NamedRange コントロールの追加\]** ダイアログ ボックスが表示されます。  
  
3.  名前付き範囲に含める 1 つ以上のセルを選びます。  
  
4.  **\[OK\]** をクリックします。  
  
     コントロールに既定の名前を付けない場合は、**\[プロパティ\]** ウィンドウで名前を変更します。  
  
#### \[データ ソース\] ウィンドウを使用してワークシートに NamedRange コントロールを追加するには  
  
1.  **\[データ ソース\]** ウィンドウを開いて、プロジェクトのデータ ソースを作成します。 詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
2.  **\[データ ソース\]** ウィンドウからワークシートにフィールドを 1 つドラッグします。  
  
     データがバインドされた <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがワークシートに追加されます。 詳細については、「[データ連結と Windows フォーム](../Topic/Data%20Binding%20and%20Windows%20Forms.md)」を参照してください。  
  
##  <a name="runtimedoclevel"></a> 実行時にドキュメント レベルのプロジェクトの NamedRange コントロールを追加する  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールは、実行時にプログラムによってワークシートに追加できます。 この方法を使用すると、イベントに応答してホスト コントロールを作成できます。 動的に作成された名前付き範囲は、ワークシートを閉じたときに、ホスト コントロールとしてワークシートに保持されません。 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
#### プログラムによってワークシートに NamedRange コントロールを追加するには  
  
1.  `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント ハンドラーに、以下のコードを挿入します。このコードでは、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをセル **A1** に追加して、その <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティを `Hello world!` に設定します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> 実行時に VSTO アドイン プロジェクトの NamedRange コントロールを追加する  
 プログラムによって <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 動的に作成された名前付き範囲は、ワークシートを閉じたときに、ホスト コントロールとしてワークシートに保持されません。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
#### プログラムによってワークシートに NamedRange コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをセル **A1** に追加して、その <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティを `Hello world` に設定します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [方法 : NamedRange コントロールのサイズを変更する](../vsto/how-to-resize-namedrange-controls.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  