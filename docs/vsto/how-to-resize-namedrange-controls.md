---
title: "方法 : NamedRange コントロールのサイズを変更する | Microsoft Docs"
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
  - "NamedRange コントロール、サイズ変更"
  - "範囲、サイズ変更 (Excel で)"
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 方法 : NamedRange コントロールのサイズを変更する
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのサイズは Microsoft Office Excel ドキュメントにコントロールを追加するときに設定できますが、後でサイズの変更が必要になる場合があります。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に名前付き範囲のサイズを変更できます。 アプリケーション レベルの VSTO アドインでも、実行時に名前付き範囲のサイズを変更できます。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時に NamedRange コントロールのサイズを変更する](#designtime)  
  
-   [実行時にドキュメント レベルのプロジェクトの NamedRange コントロールのサイズを変更する](#runtimedoclevel)  
  
-   [実行時に VSTO アドインのプロジェクトの NamedRange コントロールのサイズを変更する](#runtimeaddin)  
  
##  <a name="designtime"></a> デザイン時に NamedRange コントロールのサイズを変更する  
 名前付き範囲のサイズを変更するには、**\[名前の定義\]** ダイアログ ボックスでサイズを再定義します。  
  
#### \[名前の定義\] ダイアログ ボックスで名前付き範囲のサイズを変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを右クリックします。  
  
2.  ショートカット メニューの **\[名前付き範囲の管理\]** をクリックします。  
  
     **\[名前の定義\]** ダイアログ ボックスが表示されます。  
  
3.  サイズを変更する名前付き範囲を選択します。  
  
4.  **\[参照範囲\]** ボックスをオフにします。  
  
5.  名前付き範囲のサイズを定義するために使用するセルを選択します。  
  
6.  **\[OK\]** をクリックします。  
  
##  <a name="runtimedoclevel"></a> 実行時にドキュメント レベルのプロジェクトの NamedRange コントロールのサイズを変更する  
 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> プロパティを使用して、名前付き範囲のサイズをプログラムで変更できます。  
  
> [!NOTE]  
>  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> プロパティは読み取り専用としてマークされています。  
  
#### 名前付き範囲のサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを `Sheet1` のセル **A1** に作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#4)]  
  
2.  名前付き範囲のサイズをセル **B1** が含まれる大きさに変更します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> 実行時に VSTO アドインのプロジェクトの NamedRange コントロールのサイズを変更する  
 実行時に、任意の開いているワークシート上の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのサイズを変更できます。 VSTO アドイン を使用して <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをワークシートに追加する方法についての詳細は、「[方法 : ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)」を参照してください。  
  
#### 名前付き範囲のサイズをプログラムで変更するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを `Sheet1` のセル **A1** に作成します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#10)]  
  
2.  名前付き範囲のサイズをセル **B1** が含まれる大きさに変更します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#11)]  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法 : ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法 : Bookmark コントロールのサイズを変更する](../vsto/how-to-resize-bookmark-controls.md)   
 [方法 : ListObject コントロールのサイズを変更する](../vsto/how-to-resize-listobject-controls.md)  
  
  