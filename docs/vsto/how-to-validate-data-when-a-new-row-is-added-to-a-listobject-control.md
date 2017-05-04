---
title: "方法 : ListObject コントロールに新規行が追加された場合にデータを検証する | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発]、検証 (データを)"
  - "ListObject コントロール、新しい行"
  - "ListObject コントロール、検証 (データを)"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 方法 : ListObject コントロールに新規行が追加された場合にデータを検証する
  ユーザーはデータにバインドされている <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに新しい行を追加できます。 変更をデータ ソースにコミットする前に、ユーザーのデータを検証できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## データの検証  
 データにバインドされている <xref:Microsoft.Office.Tools.Excel.ListObject> に行が追加されるたびに、<xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> イベントが発生します。 このイベントを処理することで、データの検証を実行できます。 たとえば、アプリケーションでデータ ソースに 18 ～ 65 歳の従業員のみを追加できるようにする必要がある場合、行が追加される前に、入力された年齢がその範囲内であることを検証できます。  
  
> [!NOTE]  
>  常に、クライアントだけでなく、サーバー上のユーザー入力も確認する必要があります。 詳細については、「[安全なクライアント アプリケーション](../Topic/Secure%20Client%20Applications.md)」を参照してください。  
  
#### データ バインドされた ListObject に新規行が追加された場合にデータを検証するには  
  
1.  クラス レベルで ID および <xref:System.Data.DataTable> の変数を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  新しい <xref:System.Data.DataTable> を作成し、`Sheet1` クラス \(ドキュメント レベル プロジェクトの場合\) または `ThisAddIn` クラス \(VSTO アドイン プロジェクトの場合\) の `Startup` イベント ハンドラーにサンプルの列とデータを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  `list1_BeforeAddDataBoundRow` イベント ハンドラーに、入力された年齢が許容範囲内であるかどうかを確認するコードを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## コードのコンパイル  
 このコード例では、このコードがあるワークシートに、`list1` という名前の既存の <xref:Microsoft.Office.Tools.Excel.ListObject> があることを前提としています。  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法 : データに ListObject 列を割り当てる](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  