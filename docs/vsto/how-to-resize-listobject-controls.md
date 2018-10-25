---
title: '方法: ListObject コントロールをサイズ変更'
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
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3608399613063a0fa572fe4de12b77187f8b4b41
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811504"
---
# <a name="how-to-resize-listobject-controls"></a>方法: ListObject コントロールをサイズ変更
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズは Microsoft Office Excel ブックにコントロールを追加するときに設定しますが、後でサイズを変更することもできます。 たとえば、2 列のリストを 3 列のリストに変更できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 サイズを変更することができます<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールのデザイン時または実行時にドキュメント レベルのプロジェクト。 サイズを変更することができます<xref:Microsoft.Office.Tools.Excel.ListObject>VSTO アドイン プロジェクトでの実行時にコントロール。  
  
 このトピックでは、次のタスクについて説明します。  
  
- [デザイン時に ListObject コントロールのサイズ変更します。](#designtime)  
  
- [ドキュメント レベル プロジェクト内で実行時の ListObject コントロールをサイズ変更します。](#runtimedoclevel)  
  
- [VSTO アドイン プロジェクト内で実行時の ListObject コントロールをサイズ変更します。](#runtimeaddin)  
  
  詳細については<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを参照してください[ListObject コントロール](../vsto/listobject-control.md)します。  
  
  ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[実行時にデータ バインド リスト オブジェクトに列を操作の追加の操作方法?](http://go.microsoft.com/fwlink/?LinkID=130318)します。  
  
##  <a name="designtime"></a> デザイン時に ListObject コントロールのサイズを変更します。  
 リストのサイズを変更するには、サイズ変更ハンドルのいずれかをクリックしてドラッグでき、また **[リストのサイズ変更]** ダイアログ ボックスでそのサイズを再定義することもできます。  
  
### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>[リストのサイズ変更] ダイアログ ボックスを使用してリストのサイズを変更するには  
  
  
1.  内をクリックし、<xref:Microsoft.Office.Tools.Excel.ListObject>テーブル。 **テーブル ツール** > **デザイン**リボンのタブが表示されます。  
  
2.  [プロパティ] をクリックして**テーブルのサイズを変更する**します。  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  テーブルの新しいデータ範囲を選択します。  
  
4.  **[OK]** をクリックします。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベル プロジェクト内で実行時の ListObject コントロールのサイズを変更します。  
 サイズを変更することができます、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを使用して実行時に、<xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>メソッド。 このメソッドは、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをワークシート上の新しい位置に移動するためには使用できません。 ヘッダーは同じ行のままである必要があり、サイズを変更した <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは元のリスト オブジェクトに重なる必要があります。 サイズ変更した <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールには、ヘッダー行および少なくとも 1 つのデータ行が含まれている必要があります。  
  
### <a name="to-resize-a-list-object-programmatically"></a>リスト オブジェクトのサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> に、セル **A1** から **B3** にまたがる `Sheet1`コントロールを作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  リストのサイズをセル **A1** から **C5**までに変更します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクト内で実行時の ListObject のサイズを変更します。  
 サイズを変更することができます、<xref:Microsoft.Office.Tools.Excel.ListObject>実行時に、開いているワークシートにコントロール。 詳細を追加する方法については、 <xref:Microsoft.Office.Tools.Excel.ListObject> VSTO アドインを使用してワークシートにコントロールを参照してください[方法: ワークシートにコントロールを追加 ListObject](../vsto/how-to-add-listobject-controls-to-worksheets.md)。  
  
### <a name="to-resize-a-list-object-programmatically"></a>リスト オブジェクトのサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> に、セル **A1** から **B3** にまたがる `Sheet1`コントロールを作成します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  リストのサイズをセル **A1** から **C5**までに変更します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [方法: ワークシートに ListObject コントロールを追加](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法: Bookmark コントロールのサイズを変更します。](../vsto/how-to-resize-bookmark-controls.md)   
 [方法: NamedRange コントロールをサイズ変更](../vsto/how-to-resize-namedrange-controls.md)  
  
  