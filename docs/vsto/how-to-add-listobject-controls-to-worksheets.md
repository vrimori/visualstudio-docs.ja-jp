---
title: '方法: ワークシートに ListObject コントロールを追加します。'
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
ms.openlocfilehash: 3ab95f3929b556f6ece0d3b44ee12bad6f21a361
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>方法: ワークシートに ListObject コントロールを追加します。
  追加することができます<xref:Microsoft.Office.Tools.Excel.ListObject>デザイン時およびドキュメント レベルのプロジェクトでの実行時に、Microsoft Office Excel ワークシートにコントロールできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 追加することも<xref:Microsoft.Office.Tools.Excel.ListObject>VSTO アドイン プロジェクトでは実行時にコントロールできます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に ListObject コントロールを追加します。](#designtime)  
  
-   [ドキュメント レベルのプロジェクトの実行時に ListObject コントロールを追加します。](#runtimedoclevel)  
  
-   [VSTO アドイン プロジェクトでの実行時に ListObject コントロールを追加します。](#runtimeaddin)  
  
 詳細については<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを参照してください[ListObject コントロール](../vsto/listobject-control.md)です。  
  
##  <a name="designtime"></a> デザイン時に ListObject コントロールを追加します。  
 デザイン時にドキュメント レベルのプロジェクトのワークシートに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加する方法として、Excel から行う方法、Visual Studio の **ツールボックス**から行う方法、および **[データ ソース]** ウィンドウから行う方法があります。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-use-the-ribbon-in-excel"></a>Excel のリボンを使用するには  
  
1.  **[挿入]** タブの **[テーブル]** グループで、 **[テーブル]** をクリックします。  
  
2.  リストに含める 1 つ以上のセルを選択し、 **[OK]** をクリックします。  
  
#### <a name="to-use-the-toolbox"></a>ツールボックスを使用するには  
  
1.  **ツールボックス** の **[Excel コントロール]** タブからワークシートまで <xref:Microsoft.Office.Tools.Excel.ListObject> をドラッグします。  
  
     **[ListObject コントロールの追加]** ダイアログ ボックスが表示されます。  
  
2.  リストに含める 1 つ以上のセルを選択し、 **[OK]** をクリックします。  
  
     名前を既定のままにしない場合は、 **[プロパティ]** ウィンドウで変更します。  
  
#### <a name="to-use-the-data-sources-window"></a>[データ ソース] ウィンドウを使用するには  
  
1.  **[データ ソース]** ウィンドウを開いて、プロジェクトのデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
2.  **[データ ソース]** ウィンドウからワークシートまでテーブルをドラッグします。  
  
     データがバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがワークシートに追加されます。 詳細については、次を参照してください。[データ連結と Windows フォーム](/dotnet/framework/winforms/data-binding-and-windows-forms)です。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベルのプロジェクトの実行時に ListObject コントロールを追加します。  
 追加することができます、<xref:Microsoft.Office.Tools.Excel.ListObject>実行時に動的に制御します。 この方法を使用すると、イベントに応答してホスト コントロールを作成できます。 動的に作成されたリスト オブジェクトは、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> の `Sheet1`イベント ハンドラーに以下のコードを挿入して、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4**に追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトでの実行時に ListObject コントロールを追加します。  
 プログラムによって <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを VSTO アドイン プロジェクトの任意の開いているワークシートに追加できます。 動的に作成されたリスト オブジェクトは、ワークシートを保存して閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、次を参照してください。[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>プログラムを使用してワークシートに ListObject コントロールを追加するには  
  
1.  次のコードでは、開いているワークシートに基づいたワークシート ホスト項目を生成し、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをセル **A1** ～ **A4**に追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と実行時に VSTO アドイン内の Excel ブックを拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [拡張オブジェクトによる Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [方法: ListObject コントロールのサイズを変更します。](../vsto/how-to-resize-listobject-controls.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  