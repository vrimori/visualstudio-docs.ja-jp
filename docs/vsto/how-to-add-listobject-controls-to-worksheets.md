---
title: '方法: ワークシートに ListObject コントロールを追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 891b7fbbc4f2bf0fc0fa40fe983435a19978d081
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909061"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>方法: ワークシートに ListObject コントロールを追加します。
  追加することができます<xref:Microsoft.Office.Tools.Excel.ListObject>およびドキュメント レベルのプロジェクトでの実行時のデザイン時に、Microsoft Office Excel ワークシートにコントロール。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 追加することも<xref:Microsoft.Office.Tools.Excel.ListObject>VSTO アドイン プロジェクトでの実行時にコントロール。  
  
 このトピックでは、次のタスクについて説明します。  
  
- [デザイン時に ListObject コントロールを追加します。](#designtime)  
  
- [ドキュメント レベル プロジェクト内で実行時の ListObject コントロールを追加します。](#runtimedoclevel)  
  
- [VSTO アドイン プロジェクトでの実行時に ListObject コントロールを追加します。](#runtimeaddin)  
  
  詳細については<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを参照してください[ListObject コントロール](../vsto/listobject-control.md)します。  
  
##  <a name="designtime"></a> デザイン時に ListObject コントロールを追加します。  
 追加するいくつかの方法がある<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールをデザイン時にドキュメント レベル プロジェクト内のワークシート。Visual Studio からの Excel 内で**ツールボックス**との間、**データソース**ウィンドウ。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>Excel のリボンを使用するには  
  
1.  **[挿入]** タブの **[テーブル]** グループで、 **[テーブル]** をクリックします。  
  
2.  リストに含める 1 つ以上のセルを選択し、 **[OK]** をクリックします。  
  
#### <a name="to-use-the-toolbox"></a>ツールボックスを使用するには  
  
1.  **ツールボックス** の **[Excel コントロール]** タブからワークシートまで <xref:Microsoft.Office.Tools.Excel.ListObject> をドラッグします。  
  
     **[ListObject コントロールの追加]** ダイアログ ボックスが表示されます。  
  
2.  リストに含める 1 つ以上のセルを選択し、 **[OK]** をクリックします。  
  
     名前を既定のままにしない場合は、 **[プロパティ]** ウィンドウで変更します。  
  
#### <a name="to-use-the-data-sources-window"></a>[データ ソース] ウィンドウを使用するには  
  
1.  **[データ ソース]** ウィンドウを開いて、プロジェクトのデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)します。  
  
2.  **[データ ソース]** ウィンドウからワークシートまでテーブルをドラッグします。  
  
     データがバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがワークシートに追加されます。 詳細については、次を参照してください。[データ連結と Windows フォーム](/dotnet/framework/winforms/data-binding-and-windows-forms)します。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベル プロジェクト内で実行時の ListObject コントロールを追加します。  
 追加することができます、<xref:Microsoft.Office.Tools.Excel.ListObject>実行時に動的に制御します。 この方法を使用すると、イベントに応答してホスト コントロールを作成できます。 動的に作成されたリスト オブジェクトは、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> の `Sheet1`イベント ハンドラーに以下のコードを挿入して、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4**に追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトでの実行時に ListObject コントロールを追加します。  
 プログラムを使用して <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 動的に作成されたリスト オブジェクトは、ワークシートを保存して閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4**に追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [方法: ListObject コントロールをサイズ変更します。](../vsto/how-to-resize-listobject-controls.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
