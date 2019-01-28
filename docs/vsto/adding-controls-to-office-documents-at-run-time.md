---
title: 実行時に Office ドキュメントにコントロールを追加します。
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9dc71ba33180fa466b8d457d084faad05c61ec40
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869188"
---
# <a name="add-controls-to-office-documents-at-runtime"></a>実行時に Office ドキュメントにコントロールを追加します。
  コントロールは、Microsoft Office Word 文書と実行時に Microsoft Office Excel ブックを追加することができます。 実行時にも削除できます。 コントロールを追加または削除時に呼び出される*ダイナミック コントロール*します。  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 このトピックでは、次のことについて説明します。  

- [コントロールのコレクションを使用して実行時にコントロールを管理](#ControlsCollection)します。  

- [ホスト コントロールをドキュメントに追加](#HostControls)します。  

- [Windows フォーム コントロールをドキュメントに追加](#WindowsForms)します。  

  ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:。実行時にドキュメントの画面にコントロールを追加しますか。](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> コントロールのコレクションを使用して実行時にコントロールを管理します。  
 追加、取得、または実行時にコントロールを削除してのヘルパー メソッドを使用して、<xref:Microsoft.Office.Tools.Excel.ControlCollection>と<xref:Microsoft.Office.Tools.Word.ControlCollection>オブジェクト。  

 これらのオブジェクトにアクセスする方法は、開発しているプロジェクトの種類によって異なります。  

-   Excel のドキュメント レベルのプロジェクトでは、 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> クラス、 `Sheet1`クラス、および `Sheet2`クラスの `Sheet3` プロパティを使用します。 これらのクラスの詳細については、次を参照してください。 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)します。  

-   Word のドキュメント レベルのプロジェクトでは、 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> クラスの `ThisDocument` プロパティを使用します。 このクラスの詳細については、次を参照してください。 [Document ホスト項目](../vsto/document-host-item.md)します。  

-   Excel または Word の VSTO アドイン プロジェクトで使用して、`Controls`のプロパティを<xref:Microsoft.Office.Tools.Excel.Worksheet>または<xref:Microsoft.Office.Tools.Word.Document>実行時に生成します。 実行時にこれらのオブジェクトを生成する詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  

### <a name="add-controls"></a>コントロールを追加します。  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 型と <xref:Microsoft.Office.Tools.Word.ControlCollection> 型には、ドキュメントとワークシートにホスト コントロールや Windows フォームのコモン コントロールを追加するために使用できるヘルパー メソッドが含まれています。 各メソッドの名前は、 `Add`*コントロール クラス*という形式になっています。ここで、 *コントロール クラス* は、追加するコントロールのクラス名です。 たとえば、ドキュメントに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加するには、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> メソッドを使用します。  

 Excel のドキュメント レベルのプロジェクトで <xref:Microsoft.Office.Tools.Excel.NamedRange> を `Sheet1` に追加する方法を次のコード例に示します。  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>アクセスと削除の制御  
 <xref:Microsoft.Office.Tools.Excel.Worksheet> または <xref:Microsoft.Office.Tools.Word.Document> の `Controls` プロパティを使用すると、デザイン時に追加したコントロールを含め、ドキュメント内のすべてのコントロールを反復処理できます。 デザイン時に追加するコントロールは、 *スタティック コントロール*とも呼ばれます。  

 ダイナミック コントロールを削除するには呼び出すことによって、`Delete`方法、コントロールのまたは呼び出すことによって、`Remove`メソッドの各コントロールのコレクション。 次のコード例では、Excel のドキュメント レベルのプロジェクトで <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> メソッドを使用して <xref:Microsoft.Office.Tools.Excel.NamedRange> を `Sheet1` から削除します。  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 実行時にスタティック コントロールを削除することはできません。 `Delete` メソッドまたは `Remove` メソッドを使用してスタティック コントロールを削除しようとすると、<xref:Microsoft.Office.Tools.CannotRemoveControlException> がスローされます。  

> [!NOTE]  
>  ドキュメントの `Shutdown` イベント ハンドラーの中で、プログラムによってコントロールを削除しないでください。 `Shutdown` イベントが発生する時点では、ドキュメントの UI 要素は利用できなくなっています。 ドキュメントを閉じる前にコントロールを削除するには、Word では <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> や <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> 、Excel では <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>や <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> など、別のイベントのイベント ハンドラーにコードを追加してください。  

##  <a name="HostControls"></a> ホスト コントロールをドキュメントに追加します。  
 ホスト コントロールをプログラムでドキュメントに追加するには、そのコントロールを一意に識別する名前を指定し、ドキュメント上にコントロールを追加する場所を指定する必要があります。 具体的な手順については、次のトピックを参照してください。  

- [方法: ワークシートに ListObject コントロールを追加します。](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

- [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

- [方法: ワークシートに Chart コントロールを追加します。](../vsto/how-to-add-chart-controls-to-worksheets.md)  

- [方法: コンテンツの追加を Word 文書にコントロール](../vsto/how-to-add-content-controls-to-word-documents.md)  

- [方法: Word 文書に Bookmark コントロールを追加します。](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

  ホスト コントロールの詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。  

  ドキュメントを保存して閉じると、動的に作成したすべてのホスト コントロールはそれぞれイベントから切断され、データ バインディング機能も失われます。 ソリューションにコードを追加すれば、ドキュメントが再び開かれる時点でホスト コントロールを再作成するようにできます。 詳細については、次を参照してください。 [Office ドキュメントでのダイナミック コントロールを永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)します。  

> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>、および <xref:Microsoft.Office.Tools.Word.XMLNodes>の各ホスト コントロールは、プログラムでドキュメントに追加することができないため、ヘルパー メソッドは用意されていません。  

##  <a name="WindowsForms"></a> Windows フォーム コントロールをドキュメントに追加します。  
 Windows フォーム コントロールをプログラムでドキュメントに追加する場合は、コントロールの場所とコントロールを一意に識別する名前を指定する必要があります。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] が、各コントロールのヘルパー メソッドを提供します。 これらのメソッドはオーバーロードされているため、コントロールの場所として範囲または特定の座標のいずれかを渡すことができます。  

 ドキュメントを保存して閉じると、動的に作成されたすべての Windows フォーム コントロールはドキュメントから削除されます。 ソリューションにコードを追加すれば、ドキュメントが再び開かれる時点でコントロールを再作成するようにできます。 VSTO アドインを使用してダイナミック Windows フォーム コントロールを作成する場合は、コントロールの ActiveX ラッパーがドキュメントに残されます。 詳細については、次を参照してください。 [Office ドキュメントでのダイナミック コントロールを永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)します。  

> [!NOTE]  
>  Windows フォーム コントロールは、保護されているドキュメントにはプログラムで追加できません。 コントロールを追加するために、Word 文書または Excel ワークシートの保護をプログラムで解除する場合は、ドキュメントを閉じるときにコントロールの ActiveX ラッパーを削除するコードを追加で記述する必要があります。 コントロールの ActiveX ラッパーは、保護されたドキュメントから自動的には削除されません。  

### <a name="add-custom-controls"></a>カスタム コントロールの追加  
 カスタム ユーザー コントロールなど、使用可能なヘルパー メソッドによってサポートされていない <xref:System.Windows.Forms.Control> を追加するには、次のメソッドを使用します。  

- Excel では、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> オブジェクトの <xref:Microsoft.Office.Tools.Excel.ControlCollection> メソッドの 1 つを使用します。  

- Word では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> オブジェクトの <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドの 1 つを使用します。  

  コントロールを追加するには、<xref:System.Windows.Forms.Control>、コントロールの場所、およびコントロールを一意に識別する名前を `AddControl` メソッドに渡します。 `AddControl` メソッドは、コントロールがワークシートまたはドキュメントとどのようにやり取りするかを定義するオブジェクトを返します。 `AddControl`メソッドを返します。 を<xref:Microsoft.Office.Tools.Excel.ControlSite>(for Excel) または<xref:Microsoft.Office.Tools.Word.ControlSite>(Word) のオブジェクト。  

  次のコード例は、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> メソッドを使用して、ドキュメント レベルの Excel プロジェクトのワークシートにカスタム ユーザー コントロールを動的に追加する方法を示しています。 この例では、ユーザー コントロールの名前は `UserControl1`で、 <xref:Microsoft.Office.Interop.Excel.Range> の名前は `range1`です。 このコード例を使用するには、プロジェクトの `Sheet`*n* クラスから実行します。  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>カスタム コントロールのメンバーを使用します。  
 `AddControl` メソッドの 1 つを使用してワークシートまたは文書にコントロールを追加すると、次の 2 つの異なるコントロール オブジェクトが存在するようになります。  

- カスタム コントロールを表す <xref:System.Windows.Forms.Control> 。  

- ワークシートまたは文書に追加された後のコントロールを表す `ControlSite`、`OLEObject`、または `OLEControl` オブジェクト。  

  これらのコントロールには、共有されているプロパティやメソッドが多数あります。 これらのメンバーには、適切なコントロールを介してアクセスすることが重要です。  

- カスタム コントロールのみに属するメンバーにアクセスするには、 <xref:System.Windows.Forms.Control>を使用します。  

- 複数のコントロールで共有されているメンバーにアクセスするには、`ControlSite`、`OLEObject`、または `OLEControl` オブジェクトを使用します。  

  共有されているメンバーに <xref:System.Windows.Forms.Control>からアクセスすると、警告や通知なしに失敗したり、無効な結果が生成されたりすることがあります。 通常は `ControlSite`、`OLEObject`、または `OLEControl` オブジェクトのメソッドまたはプロパティを使用し、必要なメソッドやプロパティを使用できない場合に限って <xref:System.Windows.Forms.Control> を参照してください。  

  たとえば、`Top` プロパティは、<xref:Microsoft.Office.Tools.Excel.ControlSite> クラスと <xref:System.Windows.Forms.Control> クラスの両方に存在します。 コントロールの上端からドキュメントの先頭までの間の距離を取得または設定するには、 <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> の <xref:Microsoft.Office.Tools.Excel.ControlSite>プロパティではなく、 <xref:System.Windows.Forms.Control.Top%2A> の <xref:System.Windows.Forms.Control>プロパティを使用してください。  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Office ドキュメントでのダイナミック コントロールを永続化します。](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [方法: ワークシートに ListObject コントロールを追加します。](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法: ワークシートに Chart コントロールを追加します。](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [方法: コンテンツ コントロールを Word 文書に追加します。](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [方法: Word 文書に Bookmark コントロールを追加します。](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [方法: Office ドキュメントへの Windows フォーム コントロールを追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
