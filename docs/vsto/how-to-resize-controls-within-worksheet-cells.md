---
title: '方法: ワークシートのセル内のコントロールをサイズ変更します。'
ms.date: 02/02/2017
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
ms.openlocfilehash: 67ec290959263282c9a6f924ca9d6ba2c67b5930
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927351"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>方法: ワークシートのセル内のコントロールをサイズ変更します。
  ワークシートの列または行のサイズを変更するときに、セル内の任意のホスト コントロールが自動的にサイズが変更されたセルの幅、高さにサイズ変更します。 Windows フォーム コントロールは既定で自動的にサイズ変更されません。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 デザイン時に、コントロールを追加する場合は、各コントロールに配置オプションを設定する必要があります。  
  
 Windows フォーム コントロールをプログラムで追加して、引数を範囲指定、コントロールに自動的に、範囲内のセルのサイズが変更されたときにサイズ変更します。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
## <a name="resize-controls-at-design-time"></a>デザイン時にコントロールをサイズ変更します。  
  
### <a name="to-make-controls-resize-with-cells-at-design-time"></a>コントロールのデザイン時にセルのサイズを変更するには  
  
1.  **ツールボックス**、Windows フォーム コントロールをワークシートにドラッグします。  
  
2.  コントロールを右クリックし、をクリックし、**コントロールの書式設定**します。  
  
3.  **コントロールの書式設定**ダイアログ ボックスで、をクリックして、**プロパティ**タブ。  
  
4.  **オブジェクトの位置関係**を選択、**移動やサイズのセルで、** オプションをクリックして**ok**します。  
  
     コントロールを格納するセルのサイズを変更するときに、コントロールをセルに合わせてサイズ変更します。  
  
## <a name="resize-controls-at-runtime"></a>実行時にコントロールをサイズ変更します。  
 実行時に Windows フォーム コントロールを追加しを渡すかどうか、<xref:Microsoft.Office.Interop.Excel.Range>コントロールの場所としてコントロールが自動的にサイズを変更する範囲を含むワークシートのセルのサイズが変更されたときにします。  
  
### <a name="to-make-controls-resize-with-cells-at-run-time"></a>コントロールの実行時にセルのサイズを変更するには  
  
1.  A1 の範囲にコントロールを追加します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     コントロールを格納するセルのサイズを変更するときに、コントロールをセルに合わせてサイズ変更します。  
  
## <a name="reset-control-placement"></a>コントロールの配置をリセットします。  
 設定して、コントロールのサイズ変更および配置をリセットすることができます、`Placement`プロパティを次のいずれか<xref:Microsoft.Office.Interop.Excel.XlPlacement>値。  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>サイズを変更したり、セルに移動しないように、コントロールの動作を変更するには  
  
1.  コントロールの配置プロパティを呼び出すし、値を設定<xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [方法: Office ドキュメントへの Windows フォーム コントロールを追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法: 印刷時にワークシートのコントロールを非表示にします。](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントに Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
