---
title: Office 文書で動的コントロールを永続化します。
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
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b7544549460ab7582ce1af8fde7616213c79e9df
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692796"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Office 文書で動的コントロールを永続化します。
  文書またはブックを保存して閉じるときに、実行時に追加されるコントロールは保持されません。 厳密な動作は、ホスト コントロールと Windows フォーム コントロールで違いがあります。 どちらの場合も、ソリューションにコードを追加すれば、ユーザーが同じドキュメントを再び開く時点でコントロールが再作成されるようにできます。  
  
 実行時にドキュメントに追加するコントロールのことを、 *ダイナミック コントロール*といいます。 ダイナミック コントロールの詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="persist-host-controls-in-the-document"></a>ドキュメント内のホスト コントロールを永続化します。  
 ドキュメントを保存してから閉じるとき、すべてのダイナミック ホスト コントロールはドキュメントから削除されます。 基になるネイティブ Office オブジェクトのみが後に残ります。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールは <xref:Microsoft.Office.Interop.Excel.ListObject>になります。 ネイティブ Office オブジェクトはホスト コントロールのイベントには接続されておらず、ホスト コントロールのデータ バインディング機能を持ちません。  
  
 ホスト コントロールの種類ごとに、ドキュメントに残されるネイティブ Office オブジェクトの一覧を次の表に示します。  
  
|ホスト コントロールの種類|ネイティブ Office オブジェクトの種類|  
|-----------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>ドキュメントが開かれたときにダイナミック ホスト コントロールを作成し直す  
 ユーザーがドキュメントを開くたびに、既存のネイティブ コントロールの代わりにダイナミック ホスト コントロールを再作成することができます。 ドキュメントを開いたときにこの方法でホスト コントロールを作成すれば、ユーザーが期待するとおりの動作をシミュレートできます。  
  
 Word の場合、ホスト コントロールを再作成または<xref:Microsoft.Office.Tools.Excel.NamedRange>または<xref:Microsoft.Office.Tools.Excel.ListObject>for Excel を使用してホスト コントロールを`Add` \<*コントロール クラス*> のメソッド、<xref:Microsoft.Office.Tools.Excel.ControlCollection>または<xref:Microsoft.Office.Tools.Word.ControlCollection>オブジェクト。 ネイティブ Office オブジェクトのパラメーターを持つメソッドを使用します。  
  
 たとえば、ドキュメントが開かれた時点で既存のネイティブ <xref:Microsoft.Office.Tools.Excel.ListObject> から <xref:Microsoft.Office.Interop.Excel.ListObject> ホスト コントロールを作成するには、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> メソッドを使用し、既存の <xref:Microsoft.Office.Interop.Excel.ListObject>を渡します。 これを Excel のドキュメント レベルのプロジェクトで実行する方法を、次のコード例に示します。 このコードでは、 <xref:Microsoft.Office.Tools.Excel.ListObject> クラスの <xref:Microsoft.Office.Interop.Excel.ListObject> という名前の既存の `MyListObject` に基づいてダイナミック `Sheet1` を再作成します。  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]  
  
### <a name="re-create-chart"></a>グラフを再作成します。 
 <xref:Microsoft.Office.Tools.Excel.Chart> ホスト コントロールを再作成するには、まずネイティブの <xref:Microsoft.Office.Interop.Excel.Chart>を削除してから、 <xref:Microsoft.Office.Tools.Excel.Chart> または <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> メソッドを使用して <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> を再作成する必要があります。 ない`Add` \<*コントロール クラス*> メソッドを新規作成することができます<xref:Microsoft.Office.Tools.Excel.Chart>既存に基づいて<xref:Microsoft.Office.Interop.Excel.Chart>です。  
  
 ネイティブの <xref:Microsoft.Office.Interop.Excel.Chart>を最初に削除せずに <xref:Microsoft.Office.Tools.Excel.Chart>を再作成すると、2 つ目の重複したグラフが作成されます。  
  
## <a name="persist-windows-forms-controls-in-documents"></a>ドキュメントに Windows フォーム コントロールを永続化します。  
 ドキュメントを保存してから終了すると、動的に作成されたすべての Windows フォーム コントロールは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によってドキュメントから自動的に削除されます。 ただし、ドキュメント レベルのプロジェクトと VSTO アドイン プロジェクトでは動作が異なります。  
  
 ドキュメント レベルのカスタマイズの場合、コントロールとその基になる ActiveX ラッパー (ドキュメント上でコントロールをホストするために使用される) は、ドキュメントを次回に開いた時点で削除されます。 かつてコントロールがあったことを示すものは何も残りません。  
  
 VSTO アドインの場合、コントロールは削除されますが、ActiveX ラッパーが文書内に残ります。 ユーザーがドキュメントを次回に開くと、その ActiveX ラッパーが表示されます。 Excel では、最後にドキュメントを保存した時点で表示されていたコントロールの画像が ActiveX ラッパーに表示されます。 Word では、ActiveX ラッパーは最初は表示されませんが、ユーザーがラッパーをクリックすると、コントロールの境界を表す点線が表示されます。 ActiveX ラッパーを削除するには、いくつかの方法があります。 詳細については、次を参照してください。[アドインでの ActiveX ラッパーを削除する](#removingActiveX)です。  
  
### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>ドキュメントが開かれたときに、Windows フォーム コントロールを再作成します。  
 ユーザーがドキュメントを再び開いたときに、削除された Windows フォーム コントロールを再作成することができます。 これを行うには、ソリューションで次の手順を実行する必要があります。  
  
1.  ドキュメントを保存するか閉じるときに、コントロールのサイズ、場所、状態に関する情報を保管します。 ドキュメント レベルのカスタマイズでは、ドキュメント内のデータ キャッシュにデータを保存できます。 VSTO アドインで、ドキュメント内のカスタム XML 部分に、データを保存することができます。  
  
2.  ドキュメントを開いたときに発生するイベントで、コントロールを再作成します。 ドキュメント レベルのプロジェクトでは、 `Sheet`*n*`_Startup` または `ThisDocument_Startup` のイベント ハンドラーでこの処理を実行できます。 VSTO アドイン プロジェクトでは、 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> または <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントのイベント ハンドラーでこの処理を実行できます。  
  
###  <a name="removingActiveX"></a> アドインの ActiveX ラッパーを削除します。  
 VSTO アドインを使用してダイナミック Windows フォーム コントロールをドキュメントに追加する場合は、次の方法で、ドキュメントを次回に開いたときにコントロールの ActiveX ラッパーが表示されないようにできます。  
  
#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>ドキュメントを開いたときに、ActiveX ラッパーを削除します。  
 すべての ActiveX ラッパーを削除するには、呼び出し、`GetVstoObject`のホスト項目を生成する方法を<xref:Microsoft.Office.Interop.Word.Document>または<xref:Microsoft.Office.Interop.Excel.Workbook>新しく開かれたドキュメントを表すです。 たとえば、Word 文書からすべての ActiveX ラッパーを削除するに呼び出せる、`GetVstoObject`のホスト項目を生成する方法を<xref:Microsoft.Office.Interop.Word.Document>のイベント ハンドラーに渡されるオブジェクト、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>イベント。  
  
 この手順は、VSTO アドインがインストールされているコンピューターでのみドキュメントが開かれることがわかっている場合に便利です。 VSTO アドインをインストールしていない他のユーザーにドキュメントを渡す可能性がある場合は、代わりに、ドキュメントを閉じる前にコントロールを削除することを検討してください。  
  
 次のコード例を呼び出す方法を示しています、`GetVstoObject`メソッドは、ドキュメントが開かれているとします。  
  
 [!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
 [!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]  
  
 ただし、`GetVstoObject`メソッドが実行時に新しいホスト項目を生成するには、主に使用される、このメソッドもクリア ドキュメントからすべての ActiveX ラッパー初めて、特定のドキュメントに対して呼び出されます。 使用する方法についての詳細、`GetVstoObject`メソッドを参照してください[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
 ドキュメントを開いたときに、VSTO アドイン ダイナミック コントロールを作成する場合、VSTO アドインでは既にを呼び出すことに注意してください、`GetVstoObject`コントロールを作成するプロセスの一部としてのメソッドです。 別の呼び出しを追加する必要はありません、`GetVstoObject`このシナリオでは、ActiveX ラッパーを削除する方法です。  
  
#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>ダイナミック コントロールを削除して、文書を閉じる前に  
 VSTO アドインを使用して、ドキュメントを閉じる前にドキュメントから各ダイナミック コントロールを明示的に削除できます。 この手順は、VSTO アドインをインストールしていない他のユーザーに渡す可能性があるドキュメントの場合に便利です。  
  
 Word 文書を閉じるときに文書からすべての Windows フォーム コントロールを削除する方法を次のコード例に示します。  
  
 [!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
 [!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]  
  
## <a name="see-also"></a>関連項目  
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  