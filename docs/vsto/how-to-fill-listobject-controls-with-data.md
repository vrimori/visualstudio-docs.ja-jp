---
title: "方法 : ListObject コントロールにデータを読み込む"
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
  - "接続の解除 (データ ソースを)"
  - "ListObject コントロール、接続の解除 (データ ソースを)"
  - "ListObject コントロール、読み込み (データの)"
  - "データ [Visual Studio での Office 開発]、追加 (ワークシートへの)"
  - "データ バインディング、ListObject コントロール"
  - "ワークシート、読み込み (データを)"
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : ListObject コントロールにデータを読み込む
  データ バインディングを使用すると、ドキュメントにデータをすばやく追加できます。 リスト オブジェクトにデータをバインドした後、リスト オブジェクトを切断すると、データは表示されますが、データ ソースとのバインドは解除されます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.png "ビデオへのリンク") 関連するビデオ デモについては、「[操作方法: Excel で SharePoint リストに接続されている一覧を作成する](http://go.microsoft.com/fwlink/?LinkID=130263)」を参照してください。  
  
### ListObject コントロールにデータをバインドするには  
  
1.  クラス レベルで <xref:System.Data.DataTable> を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#20)]  
  
2.  `Sheet1` クラス \(ドキュメント レベル プロジェクトの場合\) または `ThisAddIn` クラス \(アプリケーション レベル プロジェクトの場合\) の `Startup` イベント ハンドラーにサンプルの列とデータを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#21)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> メソッドを呼び出し、列名を表示順に渡します。 リスト オブジェクト内の列の順序は、<xref:System.Data.DataTable> に表示される順序とは異なる場合があります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#22)]  
  
### データ ソースから ListObject コントロールを切断するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> の `List1` メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#23)]  
  
## コードのコンパイル  
 このコード例では、このコードがあるワークシートに、`list1` という名前の既存の <xref:Microsoft.Office.Tools.Excel.ListObject> があることを前提としています。  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法 : データに ListObject 列を割り当てる](../vsto/how-to-map-listobject-columns-to-data.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法 : データベースのデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法 : サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  