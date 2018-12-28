---
title: '方法: ワークシートに Chart コントロールを追加します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4f1c5cd15710e3886e3e8b0ed7483ba3776cef15
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648934"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>方法: ワークシートに Chart コントロールを追加します。
  追加することができます<xref:Microsoft.Office.Tools.Excel.Chart>およびドキュメント レベルのカスタマイズで実行時のデザイン時に、Microsoft Office Excel ワークシートにコントロール。 追加することも<xref:Microsoft.Office.Tools.Excel.Chart>VSTO アドインにおける実行時にコントロール。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
- [デザイン時に Chart コントロールを追加します。](#designtime)  
  
- [ドキュメント レベル プロジェクト内で実行時の Chart コントロールを追加します。](#runtimedoclevel)  
  
- [VSTO アドイン プロジェクト内で実行時の Chart コントロールを追加します。](#runtimeaddin)  
  
  詳細については<xref:Microsoft.Office.Tools.Excel.Chart>コントロールを参照してください[グラフ コントロール](../vsto/chart-control.md)します。  
  
##  <a name="designtime"></a> デザイン時に Chart コントロールを追加します。  
 アプリケーションの中からグラフを追加するのと同じ方法で、ワークシートに <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加できます。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart>コントロールはから使用できません、**ツールボックス**または**データソース**ウィンドウ。  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Excel のワークシートに Chart ホスト コントロールを追加するには  
  
1.  **挿入**] タブで、**グラフ**グループで、[**列**グラフのカテゴリをクリックします。、、およびグラフの種類をクリックします。  
  
2.  **グラフの挿入**ダイアログ ボックスで、をクリックして**OK**。  
  
3.  **デザイン**] タブで、**データ**グループで、[**データの選択**します。  
  
4.  **データ ソースの選択**ダイアログ ボックスで、クリック、**グラフ****データ範囲**ボックスし、既定の選択をオフにします。  
  
5.  **グラフのデータ**シートで、グラフのデータが含まれているセルの範囲を選択します (セル**A5**を通じて**D8**)。  
  
6.  **データ ソースの選択**ダイアログ ボックスで、をクリックして**OK**します。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベル プロジェクト内で実行時の chart コントロールを追加します。  
 追加することができます、<xref:Microsoft.Office.Tools.Excel.Chart>実行時に動的に制御します。 動的に作成したグラフは、ドキュメントを閉じるとホスト コントロールとしてドキュメントに保持されません。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに Chart コントロールを追加するには  
  
1.  `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベント ハンドラーに以下のコードを挿入して、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクト内で実行時の chart コントロールを追加します。  
 プログラムを使用して <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
 動的に作成されたグラフ コントロールは、ワークシートを閉じるとホスト コントロールとしてワークシートに保持されません。 詳細については、次を参照してください。 [Add Controls to Office は、実行時にドキュメント](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに Chart コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、<xref:Microsoft.Office.Tools.Excel.Chart> コントロールを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例の要件は以下のとおりです。  
  
-   グラフ化するデータが、ワークシートの A5 ～ D8 の範囲に格納されていること。  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [グラフ コントロール](../vsto/chart-control.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  