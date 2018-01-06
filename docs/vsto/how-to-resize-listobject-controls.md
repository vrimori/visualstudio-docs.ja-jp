---
title: "方法: ListObject コントロールのサイズを変更する |Microsoft ドキュメント"
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
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 96616338d0fd26e31ac0cc67e66d4dc35d03fdda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-listobject-controls"></a>方法 : ListObject コントロールのサイズを変更する
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズは Microsoft Office Excel ブックにコントロールを追加するときに設定しますが、後でサイズを変更することもできます。 たとえば、2 列のリストを 3 列のリストに変更できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズを変更できます。 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズを変更できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に ListObject コントロールのサイズを変更する](#designtime)  
  
-   [実行時にドキュメント レベルのプロジェクトの ListObject コントロールのサイズを変更する](#runtimedoclevel)  
  
-   [実行時に VSTO アドイン プロジェクトの ListObject コントロールのサイズを変更する](#runtimeaddin)  
  
 詳細については<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを参照してください[ListObject コントロール](../vsto/listobject-control.md)です。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: 列の追加を実行時にデータ バインド リスト オブジェクトにしますか?](http://go.microsoft.com/fwlink/?LinkID=130318)です。  
  
##  <a name="designtime"></a> デザイン時に ListObject コントロールのサイズを変更する  
 リストのサイズを変更するには、サイズ変更ハンドルのいずれかをクリックしてドラッグでき、また **[リストのサイズ変更]** ダイアログ ボックスでそのサイズを再定義することもできます。  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>[リストのサイズ変更] ダイアログ ボックスを使用してリストのサイズを変更するには  
  
  
1.  任意の場所をクリックして、<xref:Microsoft.Office.Tools.Excel.ListObject>テーブル。 **テーブル ツール]、[デザイン**をリボンにタブが表示されます。  
  
2.  [プロパティ] セクションで、をクリックして**テーブルのサイズを変更する**です。  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  テーブルに新しいデータ範囲を選択します。  
  
4.  **[OK]**をクリックします。  
  
##  <a name="runtimedoclevel"></a> 実行時にドキュメント レベルのプロジェクトの ListObject コントロールのサイズを変更する  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズは、実行時に <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> メソッドを使用して変更できます。 このメソッドは、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをワークシート上の新しい位置に移動するためには使用できません。 ヘッダーは同じ行のままである必要があり、サイズを変更した <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは元のリスト オブジェクトに重なる必要があります。 サイズ変更した <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールには、ヘッダー行および少なくとも 1 つのデータ行が含まれている必要があります。  
  
#### <a name="to-resize-a-list-object-programmatically"></a>リスト オブジェクトのサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> に、セル **A1** から **B3** にまたがる `Sheet1`コントロールを作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  リストのサイズをセル **A1** から **C5**までに変更します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> 実行時に VSTO アドイン プロジェクトの ListObject のサイズを変更する  
 実行時に、任意の開いているワークシート上の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズを変更できます。 VSTO アドインを使用して <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをワークシートに追加する方法について詳しくは、「 [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md)」をご覧ください。  
  
#### <a name="to-resize-a-list-object-programmatically"></a>リスト オブジェクトのサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> に、セル **A1** から **B3** にまたがる `Sheet1`コントロールを作成します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  リストのサイズをセル **A1** から **C5**までに変更します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>参照  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [方法: ワークシートに ListObject コントロールを追加します。](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法: Bookmark コントロールのサイズを変更します。](../vsto/how-to-resize-bookmark-controls.md)   
 [方法: NamedRange コントロールのサイズを変更する](../vsto/how-to-resize-namedrange-controls.md)  
  
  