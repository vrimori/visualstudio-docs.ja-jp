---
title: '方法: ワークシートのセル内のコントロールのサイズを変更する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b145d4435cdb295c94897424b318d328f995c340
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>方法 : ワークシートのセル内のコントロールをサイズ変更する
  ワークシートの列または行のサイズを変更するときにサイズが変更されたセルの幅と高さをセルに自動的に含まれているすべてのホスト コントロールのサイズを変更します。 Windows フォーム コントロールは既定で自動的にサイズ変更されません。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 デザイン時にコントロールを追加する場合は、各コントロールに対して配置オプションを設定する必要があります。  
  
 Windows フォーム コントロールをプログラムで追加して、範囲引数を指定して場合、コントロールに自動的に、範囲内のセルのサイズが変更されるときにサイズ変更します。 詳細については、「 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
## <a name="resizing-controls-at-design-time"></a>デザイン時にコントロールのサイズ変更  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>コントロールのデザイン時にセルのサイズを変更するには  
  
1.  **ツールボックス**、Windows フォーム コントロールをワークシートにドラッグします。  
  
2.  コントロールを右クリックし、をクリックして**コントロールの書式設定**です。  
  
3.  **コントロールの書式設定**ダイアログ ボックスで、をクリックして、**プロパティ**タブです。  
  
4.  **オブジェクトの位置関係**を選択、**セル合わせて移動やサイズ**オプションをクリックして**OK**です。  
  
     コントロールが含まれているセルのサイズを変更するときに、コントロールがセルに合わせてサイズ変更します。  
  
## <a name="resizing-controls-at-run-time"></a>実行時にコントロールのサイズ変更  
 実行時に Windows フォーム コントロールを追加しで渡すかどうか、<xref:Microsoft.Office.Interop.Excel.Range>コントロールの場所としてコントロールは自動的にサイズ変更、範囲が含まれているワークシートのセルのサイズを変更します。  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>コントロールの実行時にセルのサイズを変更するには  
  
1.  A1 の範囲にコントロールを追加します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     コントロールが含まれているセルのサイズを変更するときに、コントロールがセルに合わせてサイズ変更します。  
  
## <a name="resetting-control-placement"></a>コントロールの配置をリセットします。  
 設定して、コントロールのサイズを変更および配置をリセットすることができます、`Placement`プロパティに、次のいずれか<xref:Microsoft.Office.Interop.Excel.XlPlacement>値。  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>サイズを変更したり、セルに移動しないように、コントロールの動作を変更するには  
  
1.  コントロールの配置プロパティを呼び出すし、値を設定<xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>です。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [方法: Windows フォーム コントロールの Office ドキュメントへの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法: 印刷時にワークシートのコントロールを非表示にします。](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  