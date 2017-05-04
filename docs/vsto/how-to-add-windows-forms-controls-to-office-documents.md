---
title: "方法 : Office ドキュメントに Windows フォーム コントロールを追加する | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発], Windows フォーム コントロール"
  - "ドキュメント [Visual Studio での Office 開発], Windows フォーム コントロール"
  - "Office ドキュメント [Visual Studio での Office 開発, Windows フォーム コントロール"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], 追加"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 方法 : Office ドキュメントに Windows フォーム コントロールを追加する
  Windows フォーム コントロールは、デザイン時にドキュメント レベルのプロジェクトの Microsoft Office Excel および Microsoft Office Word のドキュメントに追加できます。  実行時には、ドキュメント レベルのカスタマイズと VSTO アドインにコントロールを追加できます。  たとえば、ユーザーがオプションの一覧から選択できるように、<xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> コントロールをワークシートに追加できます。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時のコントロールの追加](#designtime)  
  
-   [実行時のドキュメント レベルのプロジェクトでのコントロールの追加](#runtimedoclevel)  
  
-   [実行時の VSTO アドインでのコントロールの追加](#runtimeaddin)  
  
 ![ビデオへのリンク](../vsto/media/playvideo.png "ビデオへのリンク") 関連するビデオ デモについては、「[操作方法: 実行時にドキュメントにコントロールを追加する](http://go.microsoft.com/fwlink/?LinkId=132782)」をご覧ください。  
  
##  <a name="designtime"></a> デザイン時のコントロールの追加  
 デザイン時にドキュメント レベルのプロジェクトの文書に Windows フォーム コントロールを追加する方法はいくつかあります。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Windows フォーム コントロールをドキュメントにドラッグするには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。  プロジェクトの作成については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブで、追加するコントロールをクリックし、ドキュメントまでドラッグします。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、**数式バー**に  "**\=EMBED\("WinForms.Control.Host",""\)**" と表示されます。  このテキストは必要なので、削除しないでください。  
  
#### Windows フォーム コントロールをドキュメントに描画するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。  プロジェクトの作成については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブで、追加するコントロールをクリックします。  
  
3.  ドキュメント上で、コントロールの左上隅となる位置をクリックし、コントロールの右下隅となる位置までドラッグします。  
  
     指定したドキュメントの位置に、指定したサイズのコントロールが追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、**数式バー**に  "**\=EMBED\("WinForms.Control.Host",""\)**" と表示されます。  このテキストは必要なので、削除しないでください。  
  
#### シングルクリックで Windows フォーム コントロールをドキュメントに追加するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。  プロジェクトの作成については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブで、追加するコントロールをクリックします。  
  
3.  ドキュメント上で、コントロールを追加する位置をクリックします。  
  
     コントロールが既定のサイズでドキュメントに追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、**数式バー**に  "**\=EMBED\("WinForms.Control.Host",""\)**" と表示されます。  このテキストは必要なので、削除しないでください。  
  
#### ダブルクリックで Windows フォーム コントロールをドキュメントに追加するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。  プロジェクトの作成については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブで、追加するコントロールをダブルクリックします。  
  
     コントロールは、ドキュメントまたはアクティブなペインの中央に追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、**数式バー**に  "**\=EMBED\("WinForms.Control.Host",""\)**" と表示されます。  このテキストは必要なので、削除しないでください。  
  
#### Enter キーを押して Windows フォーム コントロールをドキュメントに追加するには  
  
1.  Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。  プロジェクトの作成については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブで、追加するコントロールをクリックし、Enter キーを押します。  
  
     コントロールは、ドキュメントまたはアクティブなペインの中央に追加されます。  
  
    > [!NOTE]  
    >  Excel 内でコントロールを選択すると、**数式バー**に  "**\=EMBED\("WinForms.Control.Host",""\)**" と表示されます。  このテキストは必要なので、削除しないでください。  
  
##  <a name="runtimedoclevel"></a> 実行時のドキュメント レベルのプロジェクトでのコントロールの追加  
 Windows フォーム コントロールは、実行時にプログラムを使用してドキュメントに追加できます。  Word では、`ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> プロパティのメソッドを使用します。  Excel では、`Sheet`*n* クラスの <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> プロパティのメソッドを使用します。  各メソッドにはいくつかのオーバーロードがあり、それらを使用してさまざまな方法でコントロールの場所を指定できます。  
  
 実行時にドキュメントに Windows フォーム コントロールを追加した場合、ドキュメントが閉じられると、コントロールはドキュメント内に保持されません。  次にドキュメントを開くときに、コントロールを再作成できます。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」をご覧ください。  
  
#### 実行時に Windows フォーム コントロールを追加するには  
  
1.  名前が Add\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> などの追加する Windows フォーム コントロールのクラス名\) のメソッドを使用します。  
  
     Excel のドキュメント レベルのプロジェクトで `Sheet1` のセル **C5** に <xref:Microsoft.Office.Tools.Excel.Controls.Button> を追加する方法を次のコード例に示します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> 実行時の VSTO アドインでのコントロールの追加  
 Windows フォーム コントロールは、実行時にプログラムを使用して任意の開いているドキュメントに追加できます。  まず、開いているドキュメントかワークシートに基づいたホスト項目を生成します。  次に、Word では、新しいホスト項目の <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用します。  Excel では、新しいホスト項目の <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> プロパティのメソッドを使用します。  各メソッドにはいくつかのオーバーロードがあり、それらを使用してさまざまな方法でコントロールの場所を指定できます。  
  
 実行時にドキュメントに Windows フォーム コントロールを追加した場合、ドキュメントが閉じられると、コントロールはドキュメント内に保持されません。  次にドキュメントを開くときに、コントロールを再作成できます。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」をご覧ください。  
  
 VSTO アドイン プロジェクトでのホスト項目の生成の詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」をご覧ください。  
  
#### 実行時に Windows フォーム コントロールを追加するには  
  
1.  名前が Add\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> などの追加する Windows フォーム コントロールのクラス名\) のメソッドを使用します。  
  
    > [!NOTE]  
    >  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする VSTO アドイン プロジェクトでは、Microsoft.Office.Tools.Excel.v4.0.Utilities.dll または Microsoft.Office.Tools.Word.v4.0.Utilities.dll アセンブリへの参照を先に追加する必要があります。Add\<*control class*\> メソッドへのアクセスは、その後で可能になります。  
  
     次のコード例で、Word VSTO アドインを使用して作業中のドキュメントの最初の段落に <xref:Microsoft.Office.Tools.Word.Controls.Button> を追加する方法を示します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## 参照  
 [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法 : ワークシートのセル内のコントロールをサイズ変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  