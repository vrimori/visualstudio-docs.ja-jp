---
title: "方法 : ワークシートに Chart コントロールを追加する"
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
  - "グラフ コントロール [Visual Studio での Office 開発], 追加 (ワークシートに)"
  - "コントロール [Visual Studio での Office 開発], 追加 (ワークシートに)"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 方法 : ワークシートに Chart コントロールを追加する
  <xref:Microsoft.Office.Tools.Excel.Chart> コントロールは、デザイン時および実行時にドキュメント レベルのカスタマイズの Microsoft Office Excel ワークシートに追加できます。  VSTO アドインでも、実行時に <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時の Chart コントロールの追加](#designtime)  
  
-   [Chart コントロールを実行時にドキュメント レベルのプロジェクトに追加する](#runtimedoclevel)  
  
-   [Chart コントロールを実行時に VSTO アドイン プロジェクトに追加する](#runtimeaddin)  
  
 <xref:Microsoft.Office.Tools.Excel.Chart> コントロールの詳細については、「[Chart コントロール](../vsto/chart-control.md)」をご覧ください。  
  
##  <a name="designtime"></a> デザイン時の Chart コントロールの追加  
 アプリケーションの中からグラフを追加するのと同じ方法で、ワークシートに <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加できます。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> コントロールは、**ツールボックス**や**データ ソース** ウィンドウからは使用できません。  
  
#### Excel のワークシートに Chart ホスト コントロールを追加するには  
  
1.  **\[挿入\]** タブの **\[グラフ\]** グループで、**\[縦棒\]** をクリックし、グラフのカテゴリをクリックして、目的のグラフの種類をクリックします。  
  
2.  **\[グラフの挿入\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
3.  **\[デザイン\]** タブの **\[データ\]** グループで、**\[データの選択\]** をクリックします。  
  
4.  **\[データ ソースの選択\]** ダイアログ ボックスの **\[グラフデータの範囲\]** ボックス内をクリックし、既定の選択をオフにします。  
  
5.  **グラフのデータ** シートで、グラフのデータが格納されているセルの範囲 \(セル **A5** ～ **D8**\) を選択します。  
  
6.  **\[データ ソースの選択\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
##  <a name="runtimedoclevel"></a> Chart コントロールを実行時にドキュメント レベルのプロジェクトに追加する  
 実行時に <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを動的に追加できます。  動的に作成したグラフは、ドキュメントを閉じるとホスト コントロールとしてドキュメントに保持されません。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」をご覧ください。  
  
#### プログラムを使用してワークシートに Chart コントロールを追加するには  
  
1.  `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント ハンドラーに以下のコードを挿入して、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Chart コントロールを実行時に VSTO アドイン プロジェクトに追加する  
 プログラムを使用して <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。  詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
 動的に作成されたグラフ コントロールは、ワークシートを閉じるとホスト コントロールとしてワークシートに保持されません。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」をご覧ください。  
  
#### プログラムを使用してワークシートに Chart コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## コードのコンパイル  
 この例の要件は以下のとおりです。  
  
-   グラフ化するデータが、ワークシートの A5 ～ D8 の範囲に格納されていること。  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Chart コントロール](../vsto/chart-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  