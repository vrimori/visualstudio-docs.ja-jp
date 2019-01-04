---
title: '方法: NamedRange コントロールをサイズ変更します。'
ms.date: 02/02/2017
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
ms.openlocfilehash: ac274e6e7e9a7e263e17dc03fa1c5c857f02864f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989764"
---
# <a name="how-to-resize-namedrange-controls"></a>方法: NamedRange コントロールをサイズ変更します。
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのサイズは Microsoft Office Excel ドキュメントにコントロールを追加するときに設定できますが、後でサイズの変更が必要になる場合があります。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に名前付き範囲のサイズを変更できます。 アプリケーション レベルの VSTO アドインでも、実行時に名前付き範囲のサイズを変更できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に NamedRange コントロールのサイズ変更します。](#designtime)  
  
-   [ドキュメント レベルのプロジェクトの実行時に NamedRange コントロールをサイズ変更します。](#runtimedoclevel)  
  
-   [VSTO アドイン プロジェクトでの実行時に NamedRange コントロールをサイズ変更します。](#runtimeaddin)  
  
##  <a name="designtime"></a> デザイン時に NamedRange コントロールのサイズ変更します。  
 名前付き範囲のサイズを変更するには、 **[名前の定義]** ダイアログ ボックスでサイズを再定義します。  
  
### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>[名前の定義] ダイアログ ボックスで名前付き範囲のサイズを変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを右クリックします。  
  
2.  ショートカット メニューの **[名前付き範囲の管理]** をクリックします。  
  
     **[名前の定義]** ダイアログ ボックスが表示されます。  
  
3.  サイズを変更する名前付き範囲を選択します。  
  
4.  **[参照範囲]** ボックスをオフにします。  
  
5.  名前付き範囲のサイズを定義するために使用するセルを選択します。  
  
6.  **[OK]** をクリックします。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベルのプロジェクトの実行時に NamedRange コントロールをサイズ変更します。  
 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> プロパティを使用して、名前付き範囲のサイズをプログラムで変更できます。  
  
> [!NOTE]  
>  **[プロパティ]** ウィンドウで、 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> プロパティは読み取り専用としてマークされています。  
  
### <a name="to-resize-a-named-range-programmatically"></a>名前付き範囲のサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを **のセル** A1 `Sheet1`に作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  名前付き範囲のサイズをセル **B1**が含まれる大きさに変更します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトでの実行時に NamedRange コントロールをサイズ変更します。  
 サイズを変更することができます、<xref:Microsoft.Office.Tools.Excel.NamedRange>実行時に、開いているワークシートにコントロール。 詳細を追加する方法については、 <xref:Microsoft.Office.Tools.Excel.NamedRange> VSTO アドインを使用してワークシートにコントロールを参照してください[方法。ワークシートに NamedRange コントロールを追加](../vsto/how-to-add-namedrange-controls-to-worksheets.md)します。  
  
### <a name="to-resize-a-named-range-programmatically"></a>名前付き範囲のサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを **のセル** A1 `Sheet1`に作成します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  名前付き範囲のサイズをセル **B1**が含まれる大きさに変更します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法: ブックマーク コントロールをサイズ変更します。](../vsto/how-to-resize-bookmark-controls.md)   
 [方法: ListObject コントロールをサイズ変更します。](../vsto/how-to-resize-listobject-controls.md)  
