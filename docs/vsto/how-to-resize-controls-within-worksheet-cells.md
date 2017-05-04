---
title: "方法 : ワークシートのセル内のコントロールをサイズ変更する | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発], サイズ変更"
  - "マネージ コントロール, サイズ変更"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], サイズ変更"
  - "ワークシート, サイズ変更"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 方法 : ワークシートのセル内のコントロールをサイズ変更する
  ワークシートの列や行のサイズを変更すると、セルに含まれているホスト コントロールは、サイズが変更されたセルの高さまたは幅に合わせて、自動的にサイズが変更されます。  Windows フォーム コントロールは、既定では、自動的にサイズ変更されません。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 デザイン時にコントロールを追加する場合は、コントロールごとに配置オプションを設定する必要があります。  
  
 Windows フォーム コントロールをプログラムで追加し、範囲引数を指定した場合は、範囲内のセルのサイズが変更されると、コントロールは自動的にサイズ変更されます。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
## デザイン時のコントロールのサイズ変更  
  
#### デザイン時にセルに合わせてコントロールのサイズを変更するには  
  
1.  **ツールボックス**からワークシートに Windows フォーム コントロールをドラッグします。  
  
2.  コントロールを右クリックし、**\[コントロールの書式設定\]** をクリックします。  
  
3.  **\[コントロールの書式設定\]** ダイアログ ボックスの **\[プロパティ\]** タブをクリックします。  
  
4.  **\[オブジェクトの位置関係\]** の **\[セルに合わせて移動やサイズ変更をする\]** をクリックし、**\[OK\]** をクリックします。  
  
     コントロールを含むセルのサイズを変更すると、セルに合わせてコントロールのサイズが変更されます。  
  
## 実行時のコントロールのサイズ変更  
 実行時に Windows フォーム コントロールを追加し、コントロールの場所として <xref:Microsoft.Office.Interop.Excel.Range> を渡した場合、範囲を含むワークシートのセルのサイズが変更されると、コントロールのサイズも自動的に変更されます。  
  
#### 実行時にセルに合わせてコントロールのサイズを変更するには  
  
1.  コントロールを範囲 A1 に追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     コントロールを含むセルのサイズを変更すると、セルに合わせてコントロールのサイズが変更されます。  
  
## コントロールの配置のリセット  
 `Placement` プロパティを次のいずれかの <xref:Microsoft.Office.Interop.Excel.XlPlacement> 値に設定することで、コントロールの配置とサイズ変更をリセットできます。  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### セルに合わせてコントロールのサイズが変更したり位置が移動したりしないように動作を変更するには  
  
1.  コントロールの配置プロパティを呼び出し、値を <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> に設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## 参照  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [方法 : Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法 : 印刷時にワークシートのコントロールを非表示にする](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  