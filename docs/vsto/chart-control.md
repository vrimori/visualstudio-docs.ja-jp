---
title: "Chart コントロール | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.ExcelChart"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "グラフ コントロール [Visual Studio での Office 開発]"
  - "グラフ コントロール [Visual Studio での Office 開発], データ バインド"
  - "グラフ コントロール [Visual Studio での Office 開発], イベント"
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Chart コントロール
  <xref:Microsoft.Office.Tools.Excel.Chart> コントロールはイベントを公開するグラフ オブジェクトです。  ワークシートにグラフを追加すると、ユーザーが Microsoft Office Excel オブジェクト モデルを走査する必要なく、直接、プログラムできる <xref:Microsoft.Office.Tools.Excel.Chart> オブジェクトが Visual Studio により作成されます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## コントロールの作成  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを Microsoft Office Excel ワークシートに追加できます。  
  
 VSTO アドインでは実行時に <xref:Microsoft.Office.Tools.Excel.Chart> コントロールをワークシートに追加できます。  詳細については、「[方法 : ワークシートに Chart コントロールを追加する](../vsto/how-to-add-chart-controls-to-worksheets.md)」を参照してください。  
  
> [!NOTE]  
>  動的に作成されたグラフ オブジェクトは、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。  詳細については、次のトピックを参照してください。[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
## 書式設定  
 <xref:Microsoft.Office.Interop.Excel.Chart> に適用できるすべての書式設定は、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールにも適用できます。  これには、罫線、フォント、グラフの種類、グリッド線、凡例、およびデータ ラベルが含まれます。  
  
## イベント  
 次のイベントは <xref:Microsoft.Office.Tools.Excel.Chart> コントロールに対して利用できます。  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## 参照  
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法 : ワークシートに Chart コントロールを追加する](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  