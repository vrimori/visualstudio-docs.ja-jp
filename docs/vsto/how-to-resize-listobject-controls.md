---
title: "方法 : ListObject コントロールのサイズを変更する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "コントロール [Visual Studio での Office 開発]、サイズ変更"
  - "ListObject コントロール、サイズ変更"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法 : ListObject コントロールのサイズを変更する
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズは Microsoft Office Excel ブックにコントロールを追加するときに設定しますが、後でサイズを変更することもできます。 たとえば、2 列のリストを 3 列のリストに変更できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズを変更できます。 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズを変更できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に ListObject コントロールのサイズを変更する](#designtime)  
  
-   [実行時にドキュメント レベルのプロジェクトの ListObject コントロールのサイズを変更する](#runtimedoclevel)  
  
-   [実行時に VSTO アドイン プロジェクトの ListObject コントロールのサイズを変更する](#runtimeaddin)  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールについて詳しくは、「[ListObject コントロール](../vsto/listobject-control.md)」をご覧ください。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[操作方法: 実行時にデータ バインド リスト オブジェクトに列を追加する](http://go.microsoft.com/fwlink/?LinkID=130318)」をご覧ください。  
  
##  <a name="designtime"></a> デザイン時に ListObject コントロールのサイズを変更する  
 リストのサイズを変更するには、サイズ変更ハンドルのいずれかをクリックしてドラッグでき、また **\[リストのサイズ変更\]** ダイアログ ボックスでそのサイズを再定義することもできます。  
  
#### \[リストのサイズ変更\] ダイアログ ボックスを使用してリストのサイズを変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを右クリックします。  
  
2.  ショートカット メニューの **\[リスト\]** をポイントして、**\[リストのサイズ変更\]** をクリックします。  
  
3.  リストのサイズを定義するために使用するセルを選びます。  
  
4.  **\[OK\]** をクリックします。  
  
##  <a name="runtimedoclevel"></a> 実行時にドキュメント レベルのプロジェクトの ListObject コントロールのサイズを変更する  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズは、実行時に <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> メソッドを使用して変更できます。 このメソッドは、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをワークシート上の新しい位置に移動するためには使用できません。 ヘッダーは同じ行のままである必要があり、サイズを変更した <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは元のリスト オブジェクトに重なる必要があります。 サイズ変更した <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールには、ヘッダー行および少なくとも 1 つのデータ行が含まれている必要があります。  
  
#### リスト オブジェクトのサイズをプログラムで変更するには  
  
1.  `Sheet1` に、セル **A1** から **B3** にまたがる <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  リストのサイズをセル **A1** から **C5** までに変更します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> 実行時に VSTO アドイン プロジェクトの ListObject のサイズを変更する  
 実行時に、任意の開いているワークシート上の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールのサイズを変更できます。 VSTO アドインを使用して <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをワークシートに追加する方法について詳しくは、「[方法 : ワークシートに ListObject コントロールを追加する](../vsto/how-to-add-listobject-controls-to-worksheets.md)」をご覧ください。  
  
#### リスト オブジェクトのサイズをプログラムで変更するには  
  
1.  `Sheet1` に、セル **A1** から **B3** にまたがる <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを作成します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  セル **A1** から **C5** までを含むよう、リストのサイズを変更します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [方法 : ワークシートに ListObject コントロールを追加する](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法 : Bookmark コントロールのサイズを変更する](../vsto/how-to-resize-bookmark-controls.md)   
 [方法 : NamedRange コントロールのサイズを変更する](../vsto/how-to-resize-namedrange-controls.md)  
  
  