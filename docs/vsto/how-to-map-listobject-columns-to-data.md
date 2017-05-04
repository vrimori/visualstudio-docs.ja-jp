---
title: "方法 : データに ListObject 列を割り当てる | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発]、マップ (ListObject 列に)"
  - "ListObject コントロール、マップ (データを)"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 方法 : データに ListObject 列を割り当てる
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを <xref:System.Data.DataTable> にバインドするとき、リストの中のすべての列を表示しなくてもよい場合や、データにバインドされていない特定の列が含まれている場合があります。<xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出すと、<xref:Microsoft.Office.Tools.Excel.ListObject> に表示する列をマップできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.png "ビデオへのリンク") 関連するビデオ デモについては、「[操作方法: Excel で SharePoint リストに接続されている一覧を作成する](http://go.microsoft.com/fwlink/?LinkID=130263)」をご覧ください。  
  
## 列のマッピング  
  
#### データ テーブルをリスト内の列にマップするには  
  
1.  クラス レベルで <xref:System.Data.DataTable> を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  `Sheet1` クラス \(ドキュメント レベル プロジェクトの場合\) または `ThisAddIn` クラス \(VSTO アドイン プロジェクトの場合\) の `Startup` イベント ハンドラーにサンプルの列とデータを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、表示する順序で列名を渡します。 リストのオブジェクトは新たに作成された <xref:System.Data.DataTable> にバインドされますが、リスト オブジェクト内の列の順序は、<xref:System.Data.DataTable> に表示される順序とは異なります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## マップしない列の指定  
 列を <xref:System.Data.DataTable> にマップするときに空の文字列を渡して、特定の列をデータにバインドしないことも指定できます。 そのようにすると、データにバインドされない新しい列は <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに追加されます。  
  
#### ListObject 列をマップするときにマップしない列を指定するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、表示する順序で列名を渡します。 空の文字列を使用して、マップしない列を追加する位置を示します。この場合は、タイトル列と姓の列の間です。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## コードのコンパイル  
 このコード例では、このコードがあるワークシートに、`list1` という名前の既存の <xref:Microsoft.Office.Tools.Excel.ListObject> があることを前提としています。  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法 : ListObject コントロールにデータを読み込む](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)  
  
  