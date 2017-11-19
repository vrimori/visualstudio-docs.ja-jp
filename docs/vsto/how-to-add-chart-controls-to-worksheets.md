---
title: "方法: ワークシートに Chart コントロールを追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ba31b5577090c3aef01ad974ba51a72e6f9980e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>方法 : ワークシートに Chart コントロールを追加する
  <xref:Microsoft.Office.Tools.Excel.Chart> コントロールは、デザイン時および実行時にドキュメント レベルのカスタマイズの Microsoft Office Excel ワークシートに追加できます。 VSTO アドインでも、実行時に <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時の Chart コントロールを追加します。](#designtime)  
  
-   [ドキュメント レベルのプロジェクトの実行時にグラフ コントロールを追加します。](#runtimedoclevel)  
  
-   [VSTO アドイン プロジェクトでの実行時にグラフ コントロールを追加します。](#runtimeaddin)  
  
 詳細については<xref:Microsoft.Office.Tools.Excel.Chart>コントロールを参照してください[グラフ コントロール](../vsto/chart-control.md)です。  
  
##  <a name="designtime"></a>デザイン時の Chart コントロールを追加します。  
 アプリケーションの中からグラフを追加するのと同じ方法で、ワークシートに <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加できます。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart>コントロールからは使用できない、**ツールボックス**または**データソース**ウィンドウです。  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Excel のワークシートに Chart ホスト コントロールを追加するには  
  
1.  **挿入**] タブで、**グラフ**グループで、[**列**をグラフのカテゴリをクリックし、目的のグラフの種類をクリックします。  
  
2.  **グラフの挿入**ダイアログ ボックスで、をクリックして**OK**です。  
  
3.  **デザイン**] タブで、**データ**グループで、[**データの選択**です。  
  
4.  **データ ソースの選択** ダイアログ ボックス内をクリックし、**グラフ****データ範囲**ボックスし、既定の選択をオフにします。  
  
5.  **グラフのデータ**シートで、グラフのデータが含まれるセルの範囲を選択 (セル**A5**を通じて**D8**)。  
  
6.  **データ ソースの選択**ダイアログ ボックスで、をクリックして**OK**です。  
  
##  <a name="runtimedoclevel"></a>ドキュメント レベルのプロジェクトの実行時にグラフ コントロールを追加します。  
 実行時に <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを動的に追加できます。 動的に作成したグラフは、ドキュメントを閉じるとホスト コントロールとしてドキュメントに保持されません。 詳細については、「 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに Chart コントロールを追加するには  
  
1.  `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント ハンドラーに以下のコードを挿入して、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a>VSTO アドイン プロジェクトでの実行時にグラフ コントロールを追加します。  
 プログラムを使用して <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 詳細については、「 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
 動的に作成されたグラフ コントロールは、ワークシートを閉じるとホスト コントロールとしてワークシートに保持されません。 詳細については、「 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに Chart コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例の要件は以下のとおりです。  
  
-   グラフ化するデータが、ワークシートの A5 ～ D8 の範囲に格納されていること。  
  
## <a name="see-also"></a>関連項目  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [グラフ コントロール](../vsto/chart-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  