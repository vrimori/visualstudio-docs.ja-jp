---
title: '方法: データへのマップ ListObject 列'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b77d33b8d30ed7f581e27e1cbe07d0c90715ff04
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673230"
---
# <a name="how-to-map-listobject-columns-to-data"></a>方法: データへのマップ ListObject 列
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを <xref:System.Data.DataTable>にバインドするとき、リストの中のすべての列を表示しなくてもよい場合や、データにバインドされていない特定の列が含まれている場合があります。 <xref:Microsoft.Office.Tools.Excel.ListObject> メソッドを呼び出すと、 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> に表示する列をマップできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [How do i: 作成、SharePoint リストに接続されている Excel のリスト。](http://go.microsoft.com/fwlink/?LinkID=130263)します。  
  
## <a name="map-columns"></a>列のマップ  
  
### <a name="to-map-a-data-table-to-columns-in-a-list"></a>データ テーブルをリスト内の列にマップするには  
  
1.  クラス レベルで <xref:System.Data.DataTable> を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  サンプルの列とデータを追加、`Startup`のイベント ハンドラー、 `Sheet1` (ドキュメント レベルのプロジェクト) 内のクラスまたは`ThisAddIn`クラス (VSTO アドイン プロジェクトの場合)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、列名を表示順に渡します。 リスト オブジェクトがバインドされる、新しく作成した<xref:System.Data.DataTable>に表示される順序と、リスト オブジェクト内の列の順序が異なりますが、<xref:System.Data.DataTable>します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specify-unmapped-columns"></a>マップされていない列を指定します  
 列を <xref:System.Data.DataTable>にマップするときに空の文字列を渡して、特定の列をデータにバインドしないことも指定できます。 そのようにすると、データにバインドされない新しい列は <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに追加されます。  
  
### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>ListObject 列をマップするときにマップしない列を指定するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、列名を表示順に渡します。 空の文字列を使用して、マップしない列を追加する位置を示します。この場合は、タイトル列と姓の列の間です。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 このコード例では、このコードがあるワークシートに、 <xref:Microsoft.Office.Tools.Excel.ListObject> という名前の既存の `list1` があることを前提としています。  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法: 塗りつぶし ListObject コントロール データ](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)  
  
  