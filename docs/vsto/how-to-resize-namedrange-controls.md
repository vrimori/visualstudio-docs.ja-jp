---
title: '方法: NamedRange コントロールのサイズを変更する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d475f9140607ba0ae7415a60a9589aef11a44a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-namedrange-controls"></a>方法 : NamedRange コントロールのサイズを変更する
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのサイズは Microsoft Office Excel ドキュメントにコントロールを追加するときに設定できますが、後でサイズの変更が必要になる場合があります。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に名前付き範囲のサイズを変更できます。 アプリケーション レベルの VSTO アドインでも、実行時に名前付き範囲のサイズを変更できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に NamedRange コントロールのサイズを変更する](#designtime)  
  
-   [実行時にドキュメント レベルのプロジェクトの NamedRange コントロールのサイズを変更する](#runtimedoclevel)  
  
-   [実行時に VSTO アドインのプロジェクトの NamedRange コントロールのサイズを変更する](#runtimeaddin)  
  
##  <a name="designtime"></a> Resizing NamedRange Controls at Design Time  
 名前付き範囲のサイズを変更するには、 **[名前の定義]** ダイアログ ボックスでサイズを再定義します。  
  
#### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>[名前の定義] ダイアログ ボックスで名前付き範囲のサイズを変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを右クリックします。  
  
2.  ショートカット メニューの **[名前付き範囲の管理]** をクリックします。  
  
     **[名前の定義]** ダイアログ ボックスが表示されます。  
  
3.  サイズを変更する名前付き範囲を選択します。  
  
4.  **[参照範囲]** ボックスをオフにします。  
  
5.  名前付き範囲のサイズを定義するために使用するセルを選択します。  
  
6.  **[OK]**をクリックします。  
  
##  <a name="runtimedoclevel"></a> Resizing NamedRange Controls at Run Time in a Document-Level Project  
 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> プロパティを使用して、名前付き範囲のサイズをプログラムで変更できます。  
  
> [!NOTE]  
>  **[プロパティ]** ウィンドウで、 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> プロパティは読み取り専用としてマークされています。  
  
#### <a name="to-resize-a-named-range-programmatically"></a>名前付き範囲のサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを **のセル** A1 `Sheet1`に作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  名前付き範囲のサイズをセル **B1**が含まれる大きさに変更します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Resizing NamedRange Controls at Run Time in an VSTO Add-in project  
 実行時に、任意の開いているワークシート上の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのサイズを変更できます。 VSTO アドイン を使用して <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをワークシートに追加する方法についての詳細は、「 [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md)をクリックします。  
  
#### <a name="to-resize-a-named-range-programmatically"></a>名前付き範囲のサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを **のセル** A1 `Sheet1`に作成します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  名前付き範囲のサイズをセル **B1**が含まれる大きさに変更します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法: Bookmark コントロールのサイズを変更します。](../vsto/how-to-resize-bookmark-controls.md)   
 [方法: ListObject コントロールのサイズを変更する](../vsto/how-to-resize-listobject-controls.md)  
  
  