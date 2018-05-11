---
title: '方法: ワークシートに ListObject コントロールを追加する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55d3a26f0fbf02556071dfc16d08357519b5cff9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>方法 : ワークシートに ListObject コントロールを追加する
  ドキュメント レベルのプロジェクトでは、デザイン時および実行時に、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを Microsoft Office Excel ワークシートに追加できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドイン プロジェクトでも、実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時の ListObject コントロールの追加](#designtime)  
  
-   [ドキュメント レベルのプロジェクトで、ListObject コントロールを実行時に追加する](#runtimedoclevel)  
  
-   [VSTO アドイン プロジェクトで、ListObject コントロールを実行時に追加する](#runtimeaddin)  
  
 詳細については<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを参照してください[ListObject コントロール](../vsto/listobject-control.md)です。  
  
##  <a name="designtime"></a> Adding ListObject Controls at Design Time  
 デザイン時にドキュメント レベルのプロジェクトのワークシートに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加する方法として、Excel から行う方法、Visual Studio の **ツールボックス**から行う方法、および **[データ ソース]** ウィンドウから行う方法があります。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-use-the-ribbon-in-excel"></a>Excel のリボンを使用するには  
  
1.  **[挿入]** タブの **[テーブル]** グループで、 **[テーブル]**をクリックします。  
  
2.  リストに含める 1 つ以上のセルを選択し、 **[OK]**をクリックします。  
  
#### <a name="to-use-the-toolbox"></a>ツールボックスを使用するには  
  
1.  **ツールボックス** の **[Excel コントロール]**タブからワークシートまで <xref:Microsoft.Office.Tools.Excel.ListObject> をドラッグします。  
  
     **[ListObject コントロールの追加]** ダイアログ ボックスが表示されます。  
  
2.  リストに含める 1 つ以上のセルを選択し、 **[OK]**をクリックします。  
  
     名前を既定のままにしない場合は、 **[プロパティ]** ウィンドウで変更します。  
  
#### <a name="to-use-the-data-sources-window"></a>[データ ソース] ウィンドウを使用するには  
  
1.  **[データ ソース]** ウィンドウを開いて、プロジェクトのデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
2.  **[データ ソース]** ウィンドウからワークシートまでテーブルをドラッグします。  
  
     データがバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがワークシートに追加されます。 詳細については、「 [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)」を参照してください。  
  
##  <a name="runtimedoclevel"></a> Adding ListObject Controls at Run Time in a Document-Level Project  
 実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを動的に追加できます。 この方法を使用すると、イベントに応答してホスト コントロールを作成できます。 動的に作成されたリスト オブジェクトは、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、「 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> の `Sheet1`イベント ハンドラーに以下のコードを挿入して、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4**に追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Adding ListObject Controls at Run Time in an VSTO Add-in project  
 プログラムによって <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 動的に作成されたリスト オブジェクトは、ワークシートを保存して閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、「 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4**に追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>関連項目  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [方法: ListObject コントロールのサイズを変更します。](../vsto/how-to-resize-listobject-controls.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  