---
title: '方法: データに ListObject コントロールを塗りつぶす'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a41c9c630eb95fbd0fed2b9ca2f05d56eff65c44
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865585"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>方法: データに ListObject コントロールを塗りつぶす
  データ バインディングを使用すると、ドキュメントにデータをすばやく追加できます。 リスト オブジェクトにデータをバインドした後、リスト オブジェクトを切断すると、データは表示されますが、データ ソースとのバインドは解除されます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:。SharePoint リストに接続されている Excel でリストを作成しますか。](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### <a name="to-bind-data-to-a-listobject-control"></a>ListObject コントロールにデータをバインドするには  
  
1.  クラス レベルで <xref:System.Data.DataTable> を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  `Startup` クラス (ドキュメント レベル プロジェクトの場合) または `Sheet1` クラス (アプリケーション レベル プロジェクトの場合) の `ThisAddIn` イベント ハンドラーにサンプルの列とデータを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、列名を表示順に渡します。 リスト オブジェクト内の列の順序は、 <xref:System.Data.DataTable>に表示される順序とは異なる場合があります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>データ ソースから ListObject コントロールを切断するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> の `List1`メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 このコード例では、このコードがあるワークシートに、 <xref:Microsoft.Office.Tools.Excel.ListObject> という名前の既存の `list1` があることを前提としています。  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法: データに ListObject 列をマップします。](../vsto/how-to-map-listobject-columns-to-data.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法: サービスからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)  
