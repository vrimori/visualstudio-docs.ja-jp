---
title: "Office ドキュメントでのダイナミック コントロールの永続化"
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
  - "Office ドキュメント [Visual Studio での Office 開発]、Windows フォーム コントロール"
  - "Office ドキュメント [Visual Studio での Office 開発、ホスト コントロール"
  - "コントロール [Visual Studio での Office 開発]、ドキュメントでの永続化"
  - "Windows フォーム コントロール [Visual Studio での Office 開発]、ドキュメントでの永続化"
  - "ドキュメント [Visual Studio での Office 開発]、Windows フォーム コントロール"
  - "ドキュメント [Visual Studio での Office 開発]、ホスト コントロール"
  - "ホスト コントロール [Visual Studio での Office 開発]、ドキュメントでの永続化"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Office ドキュメントでのダイナミック コントロールの永続化
  実行時に追加されたコントロールは、ドキュメントまたはブックを保存するとき、および閉じるときに永続化されません。 厳密な動作は、ホスト コントロールと Windows フォーム コントロールで違いがあります。 どちらの場合も、ソリューションにコードを追加すれば、ユーザーが同じドキュメントを再び開く時点でコントロールが再作成されるようにできます。  
  
 実行時にドキュメントに追加するコントロールのことを、*ダイナミック コントロール*といいます。 ダイナミック コントロールについて詳しくは、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## ドキュメントでホスト コントロールを永続化する  
 ドキュメントを保存してから閉じるとき、すべてのダイナミック ホスト コントロールはドキュメントから削除されます。 基になるネイティブ Office オブジェクトのみが後に残ります。 たとえば、<xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールは <xref:Microsoft.Office.Interop.Excel.ListObject> になります。 ネイティブ Office オブジェクトはホスト コントロールのイベントには接続されておらず、ホスト コントロールのデータ バインディング機能を持ちません。  
  
 ホスト コントロールの種類ごとに、ドキュメントに残されるネイティブ Office オブジェクトの一覧を次の表に示します。  
  
|ホスト コントロールの種類|ネイティブ Office オブジェクトの種類|  
|-------------------|----------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### ドキュメントが開かれた時点でダイナミック ホスト コントロールを再作成する  
 ユーザーがドキュメントを開くたびに、既存のネイティブ コントロールの代わりにダイナミック ホスト コントロールを再作成することができます。 ドキュメントを開いたときにこの方法でホスト コントロールを作成すれば、ユーザーが期待するとおりの動作をシミュレートできます。  
  
 Word のホスト コントロール、または Excel の <xref:Microsoft.Office.Tools.Excel.NamedRange> または <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールを再作成するには、<xref:Microsoft.Office.Tools.Excel.ControlCollection> または <xref:Microsoft.Office.Tools.Word.ControlCollection> オブジェクトの `Add`\<*control class*\> メソッドを使用します。 ネイティブ Office オブジェクトのパラメーターを持つメソッドを使用します。  
  
 たとえば、ドキュメントが開かれた時点で既存のネイティブ <xref:Microsoft.Office.Interop.Excel.ListObject> から <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールを作成するには、<xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> メソッドを使用し、既存の <xref:Microsoft.Office.Interop.Excel.ListObject> を渡します。 これを Excel のドキュメント レベルのプロジェクトで実行する方法を、次のコード例に示します。 このコードでは、`Sheet1` クラスの `MyListObject` という名前の既存の <xref:Microsoft.Office.Interop.Excel.ListObject> に基づいてダイナミック <xref:Microsoft.Office.Tools.Excel.ListObject> を再作成します。  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### グラフを再作成する  
 <xref:Microsoft.Office.Tools.Excel.Chart> ホスト コントロールを再作成するには、まずネイティブの <xref:Microsoft.Office.Interop.Excel.Chart> を削除してから、<xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> または <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> メソッドを使用して <xref:Microsoft.Office.Tools.Excel.Chart> を再作成する必要があります。 既存の <xref:Microsoft.Office.Interop.Excel.Chart> に基づいて新しい <xref:Microsoft.Office.Tools.Excel.Chart> を作成できる `Add`\<*control class*\> メソッドはありません。  
  
 ネイティブの <xref:Microsoft.Office.Interop.Excel.Chart> を最初に削除せずに <xref:Microsoft.Office.Tools.Excel.Chart> を再作成すると、2 つ目の重複したグラフが作成されます。  
  
## ドキュメントで Windows フォーム コントロールを永続化する  
 ドキュメントを保存してから終了すると、動的に作成されたすべての Windows フォーム コントロールは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によってドキュメントから自動的に削除されます。 ただし、ドキュメント レベルのプロジェクトと VSTO アドイン プロジェクトでは動作が異なります。  
  
 ドキュメント レベルのカスタマイズの場合、コントロールとその基になる ActiveX ラッパー \(ドキュメント上でコントロールをホストするために使用される\) は、ドキュメントを次回に開いた時点で削除されます。 かつてコントロールがあったことを示すものは何も残りません。  
  
 VSTO アドインの場合、コントロールは削除されますが、ActiveX ラッパーが文書内に残ります。 ユーザーがドキュメントを次回に開くと、その ActiveX ラッパーが表示されます。 Excel では、最後にドキュメントを保存した時点で表示されていたコントロールの画像が ActiveX ラッパーに表示されます。 Word では、ActiveX ラッパーは最初は表示されませんが、ユーザーがラッパーをクリックすると、コントロールの境界を表す点線が表示されます。 ActiveX ラッパーを削除するには、いくつかの方法があります。 詳細については、「[アドインからの ActiveX ラッパーの削除](#removingActiveX)」を参照してください。  
  
### ドキュメントが開かれた時点で Windows フォーム コントロールを再作成する  
 ユーザーがドキュメントを再び開いたときに、削除された Windows フォーム コントロールを再作成することができます。 これを行うには、ソリューションで次の手順を実行する必要があります。  
  
1.  ドキュメントを保存するか閉じるときに、コントロールのサイズ、場所、状態に関する情報を保管します。 ドキュメント レベルのカスタマイズでは、このデータをドキュメントのデータ キャッシュに保存できます。 VSTO アドインでは、このデータをドキュメントのカスタム XML 部分に保存できます。  
  
2.  ドキュメントを開いたときに発生するイベントで、コントロールを再作成します。 ドキュメント レベルのプロジェクトでは、`Sheet`*n*`_Startup` または `ThisDocument_Startup` のイベント ハンドラーでこの処理を実行できます。 VSTO アドイン プロジェクトでは、<xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> または <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントのイベント ハンドラーでこの処理を実行できます。  
  
###  <a name="removingActiveX"></a> アドインの ActiveX ラッパーを削除する  
 VSTO アドインを使用してダイナミック Windows フォーム コントロールをドキュメントに追加する場合は、次の方法で、ドキュメントを次回に開いたときにコントロールの ActiveX ラッパーが表示されないようにできます。  
  
#### ドキュメントが開かれたときに ActiveX ラッパーを削除する  
 すべての ActiveX ラッパーを削除するには、GetVstoObject メソッドを呼び出して、新しく開いたドキュメントを表す <xref:Microsoft.Office.Interop.Word.Document> または <xref:Microsoft.Office.Interop.Excel.Workbook> のためのホスト項目を生成します。 たとえば、Word 文書からすべての ActiveX ラッパーを削除するには、GetVstoObject メソッドを呼び出して <xref:Microsoft.Office.Interop.Word.Document> オブジェクトのためのホスト項目を生成し、そのオブジェクトを <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントのイベント ハンドラーに渡します。  
  
 この手順は、VSTO アドインがインストールされているコンピューターでのみドキュメントが開かれることがわかっている場合に便利です。 VSTO アドインをインストールしていない他のユーザーにドキュメントを渡す可能性がある場合は、代わりに、ドキュメントを閉じる前にコントロールを削除することを検討してください。  
  
 ドキュメントが開かれたときに GetVstoObject メソッドを呼び出す方法を次のコード例に示します。  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 GetVstoObject メソッドは主として実行時に新しいホスト項目を生成するために使用しますが、ドキュメントに対してこのメソッドを初めて呼び出したときに、ドキュメントからすべての ActiveX ラッパーがクリアされるという効果もあります。GetVstoObject メソッドの使用方法の詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
 ドキュメントが開かれたときに VSTO アドインがダイナミック コントロールを作成する場合、コントロールの作成プロセスの一部として VSTO アドインにより既に GetVstoObject メソッドが呼び出されています。 このシナリオでは、ActiveX ラッパーを削除するために GetVstoObject メソッドに対する別個の呼び出しを追加する必要はありません。  
  
#### ドキュメントを閉じる前にダイナミック コントロールを削除する  
 VSTO アドインを使用して、ドキュメントを閉じる前にドキュメントから各ダイナミック コントロールを明示的に削除できます。 この手順は、VSTO アドインをインストールしていない他のユーザーに渡す可能性があるドキュメントの場合に便利です。  
  
 Word 文書を閉じるときに文書からすべての Windows フォーム コントロールを削除する方法を次のコード例に示します。  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## 参照  
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  