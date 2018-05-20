---
title: '方法: Office ドキュメントへの Windows フォーム コントロールの追加'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fcff642f75da15f649cc7e3ab525b4db0ac1c83
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>方法: Office ドキュメントへの Windows フォーム コントロールの追加
  Windows フォーム コントロールは、デザイン時にドキュメント レベルのプロジェクトの Microsoft Office Excel および Microsoft Office Word のドキュメントに追加できます。 ドキュメント レベルのカスタマイズおよび VSTO アドインで、実行時にコントロールを追加できます。たとえば、ユーザーがオプションの一覧から選択できるように、<xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> コントロールをワークシートに追加できます。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時にコントロールを追加します。](#designtime)  
  
-   [ドキュメント レベルのプロジェクトでの実行時にコントロールを追加します。](#runtimedoclevel)  
  
-   [VSTO アドインにおける実行時にコントロールを追加します。](#runtimeaddin)  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は、ドキュメントにコントロールを i: 追加画面実行時にしますか?](http://go.microsoft.com/fwlink/?LinkId=132782)です。  
  
##  <a name="designtime"></a> デザイン時にコントロールを追加します。  
 デザイン時にドキュメント レベルのプロジェクトの文書に Windows フォーム コントロールを追加する方法はいくつかあります。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Windows フォーム コントロールをドキュメントにドラッグするには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトを作成する方法については、次を参照してください。[する方法: Visual Studio で作成する Office プロジェクト](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**を追加するコントロールをクリックし、ドキュメントにドラッグします。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Windows フォーム コントロールをドキュメントに描画するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトを作成する方法については、次を参照してください。[する方法: Visual Studio で作成する Office プロジェクト](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、追加するコントロールをクリックします。  
  
3.  ドキュメント上で、コントロールの左上隅となる位置をクリックし、コントロールの右下隅となる位置までドラッグします。  
  
     指定したドキュメントの位置に、指定したサイズのコントロールが追加されます。  
  
    > [!NOTE]  
    >  Excel で、コントロールを選択すると表示されます **=EMBED("WinForms.Control.Host","")** で、**数式バー**です。 このテキストは必要なので、削除しないでください。  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>シングルクリックで Windows フォーム コントロールをドキュメントに追加するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトを作成する方法については、次を参照してください。[する方法: Visual Studio で作成する Office プロジェクト](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、追加するコントロールをクリックして  
  
3.  ドキュメント上で、コントロールを追加する位置をクリックします。  
  
     コントロールが既定のサイズでドキュメントに追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>ダブルクリックで Windows フォーム コントロールをドキュメントに追加するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトを作成する方法については、次を参照してください。[する方法: Visual Studio で作成する Office プロジェクト](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、追加するコントロールをダブルクリックします。  
  
     コントロールは、ドキュメントまたはアクティブなペインの中央に追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Enter キーを押すと、ドキュメントに Windows フォーム コントロールを追加するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトを作成する方法については、次を参照してください。[する方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**を追加して、キーを押すコントロールをクリックして、 **Enter**キー。  
  
     コントロールは、ドキュメントまたはアクティブなペインの中央に追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベルのプロジェクトでの実行時にコントロールを追加します。  
 プログラムで、実行時にドキュメントに Windows フォーム コントロールを追加することができます。 Word では、`ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> プロパティのメソッドを使用します。 Excel でのメソッドを使用して、<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A>のプロパティ、 `Sheet` *n*クラスです。 各メソッドにはいくつかのオーバーロードがあり、それらを使用してさまざまな方法でコントロールの場所を指定できます。  
  
 実行時にドキュメントに Windows フォーム コントロールを追加するときに、ドキュメントが閉じられたときにコントロールはドキュメントに保持されません。 次にドキュメントを開くときに、コントロールを再作成できます。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>実行時に Windows フォーム コントロールを追加するには  
  
1.  追加の名前を持つメソッドを使用して\<*コントロール クラス*> (ここで*コントロール クラス*など、追加する Windows フォーム コントロールのクラス名は、 <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>)。  
  
     次のコード例は、追加する方法を示します、<xref:Microsoft.Office.Tools.Excel.Controls.Button>セルに**C5**の`Sheet1`Excel 用ドキュメント レベルのプロジェクトです。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> VSTO アドインにおける実行時にコントロールを追加します。  
 実行時に開いている文書には、Windows フォーム コントロールをプログラムで追加できます。 まず、開いているドキュメントかワークシートに基づいたホスト項目を生成します。 次に、Word では、新しいホスト項目の <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用します。 Excel では、新しいホスト項目の <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> プロパティのメソッドを使用します。 各メソッドにはいくつかのオーバーロードがあり、それらを使用してさまざまな方法でコントロールの場所を指定できます。  
  
 実行時にドキュメントに Windows フォーム コントロールを追加するときに、ドキュメントが閉じられたときにコントロールはドキュメントに保持されません。 次にドキュメントを開くときに、コントロールを再作成できます。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
 VSTO アドイン プロジェクトでホスト項目の生成の詳細については、次を参照してください。[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>実行時に Windows フォーム コントロールを追加するには  
  
1.  追加の名前を持つメソッドを使用して\<*コントロール クラス*> (ここで*コントロール クラス*など、追加する Windows フォーム コントロールのクラス名は、 <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>)。  
  
    > [!NOTE]  
    >  プロジェクトをターゲットとする VSTO アドインで、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]か、後への参照を追加する必要があります、 *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll*または*Microsoft.Office.Tools.Word.v4.0.Utilities.dll*アセンブリの追加 にアクセスできるように\<*コントロール クラス*> メソッドです。  
  
     次のコード例で、Word VSTO アドインを使用して作業中のドキュメントの最初の段落に <xref:Microsoft.Office.Tools.Word.Controls.Button> を追加する方法を示します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントの概要 Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法: ワークシートのセル内のコントロールのサイズを変更します。](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  