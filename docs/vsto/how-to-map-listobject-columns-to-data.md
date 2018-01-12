---
title: "方法: データに ListObject 列をマップ |Microsoft ドキュメント"
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
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c8def85e851ac6a51eef59e3f0538025f0e7ce6c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-listobject-columns-to-data"></a>方法 : データに ListObject 列を割り当てる
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを <xref:System.Data.DataTable>にバインドするとき、リストの中のすべての列を表示しなくてもよい場合や、データにバインドされていない特定の列が含まれている場合があります。 <xref:Microsoft.Office.Tools.Excel.ListObject> メソッドを呼び出すと、 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> に表示する列をマップできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[操作方法: 作成、一覧は、SharePoint リストに接続されている Excel のですか?](http://go.microsoft.com/fwlink/?LinkID=130263)です。  
  
## <a name="mapping-columns"></a>列のマッピング  
  
#### <a name="to-map-a-data-table-to-columns-in-a-list"></a>データ テーブルをリスト内の列にマップするには  
  
1.  クラス レベルで <xref:System.Data.DataTable> を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  `Startup` クラス (ドキュメント レベル プロジェクトの場合) または `Sheet1` クラス (VSTO アドイン プロジェクトの場合) の `ThisAddIn` イベント ハンドラーにサンプルの列とデータを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、表示する順序で列名を渡します。 リストのオブジェクトは新たに作成された <xref:System.Data.DataTable>にバインドされますが、リスト オブジェクト内の列の順序は、 <xref:System.Data.DataTable>に表示される順序とは異なります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specifying-unmapped-columns"></a>マップしない列の指定  
 列を <xref:System.Data.DataTable>にマップするときに空の文字列を渡して、特定の列をデータにバインドしないことも指定できます。 そのようにすると、データにバインドされない新しい列は <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに追加されます。  
  
#### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>ListObject 列をマップするときにマップしない列を指定するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、列名を表示順に渡します。 空の文字列を使用して、マップしない列を追加する位置を示します。この場合は、タイトル列と姓の列の間です。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例では、このコードがあるワークシートに、 <xref:Microsoft.Office.Tools.Excel.ListObject> という名前の既存の `list1` があることを前提としています。  
  
## <a name="see-also"></a>参照  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法: ListObject コントロールにデータを入力](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)  
  
  