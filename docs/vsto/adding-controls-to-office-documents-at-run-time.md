---
title: 実行時に Office ドキュメントへのコントロールの追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
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
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f36e98d79f8037aba2a2f1a50d9a7fb3915a94c
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="adding-controls-to-office-documents-at-run-time"></a>実行時の Office ドキュメントへのコントロールの追加
  コントロールは、実行時に、Microsoft Office Word 文書と Microsoft Office Excel ブックに追加できます。 それらを実行時に削除することもできます。 実行時にドキュメントに追加したりドキュメントから削除したりするコントロールのことを、 *ダイナミック コントロール*といいます。  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 このトピックでは、次のことについて説明します。  

-   [コントロール コレクションを使用して実行時にコントロールを管理する](#ControlsCollection)。  

-   [ホスト コントロールをドキュメントに追加する](#HostControls)。  

-   [Windows フォーム コントロールをドキュメントに追加する](#WindowsForms)。  

 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: コントロールの追加を実行時にドキュメントの画面に?](http://go.microsoft.com/fwlink/?LinkId=132782)です。  

##  <a name="ControlsCollection"></a> Managing Controls at Run Time by Using the Control Collections  
 実行時にコントロールを追加、取得、または削除するには、 <xref:Microsoft.Office.Tools.Excel.ControlCollection> オブジェクトと <xref:Microsoft.Office.Tools.Word.ControlCollection> オブジェクトのヘルパー メソッドを使用します。  

 これらのオブジェクトにアクセスする方法は、開発しているプロジェクトの種類によって異なります。  

-   Excel のドキュメント レベルのプロジェクトでは、 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> クラス、 `Sheet1`クラス、および `Sheet2`クラスの `Sheet3` プロパティを使用します。 これらのクラスの詳細については、次を参照してください。 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)です。  

-   Word のドキュメント レベルのプロジェクトでは、 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> クラスの `ThisDocument` プロパティを使用します。 このクラスの詳細については、次を参照してください。 [Document ホスト項目](../vsto/document-host-item.md)です。  

-   Excel または Word の VSTO アドイン プロジェクトでは、コントロール プロパティを使用して、<xref:Microsoft.Office.Tools.Excel.Worksheet>または<xref:Microsoft.Office.Tools.Word.Document>実行時に生成します。 詳細については、実行時にこれらのオブジェクトを生成する、次を参照してください。 [Word 文書や拡張を実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  

### <a name="adding-controls"></a>コントロールの追加  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 型と <xref:Microsoft.Office.Tools.Word.ControlCollection> 型には、ドキュメントとワークシートにホスト コントロールや Windows フォームのコモン コントロールを追加するために使用できるヘルパー メソッドが含まれています。 各メソッドの名前は、 `Add`*コントロール クラス*という形式になっています。ここで、 *コントロール クラス* は、追加するコントロールのクラス名です。 たとえば、ドキュメントに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加するには、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> メソッドを使用します。  

 Excel のドキュメント レベルのプロジェクトで <xref:Microsoft.Office.Tools.Excel.NamedRange> を `Sheet1` に追加する方法を次のコード例に示します。  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="accessing-and-deleting-controls"></a>コントロールのアクセスと削除  
 コントロール プロパティを使用することができます、<xref:Microsoft.Office.Tools.Excel.Worksheet>または<xref:Microsoft.Office.Tools.Word.Document>をデザイン時に追加したコントロールを含め、ドキュメント内のすべてのコントロールを反復処理します。 デザイン時に追加するコントロールは、 *スタティック コントロール*とも呼ばれます。  

 コントロールの Delete メソッドを呼び出すことによって、または各コントロール コレクションの Remove メソッドを呼び出すことにより、ダイナミック コントロールを削除できます。 次のコード例では、Excel のドキュメント レベルのプロジェクトで <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> メソッドを使用して <xref:Microsoft.Office.Tools.Excel.NamedRange> を `Sheet1` から削除します。  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 実行時にスタティック コントロールを削除することはできません。 メソッドを使用して、削除、または削除が静的なコントロールを削除しようとすると、<xref:Microsoft.Office.Tools.CannotRemoveControlException>がスローされます。  

> [!NOTE]  
>  ドキュメントの `Shutdown` イベント ハンドラーの中で、プログラムによってコントロールを削除しないでください。 `Shutdown` イベントが発生する時点では、ドキュメントの UI 要素は利用できなくなっています。 ドキュメントを閉じる前にコントロールを削除するには、Word では <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> や <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> 、Excel では <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>や <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> など、別のイベントのイベント ハンドラーにコードを追加してください。  

##  <a name="HostControls"></a> Adding Host Controls to Documents  
 ホスト コントロールをプログラムでドキュメントに追加するには、そのコントロールを一意に識別する名前を指定し、ドキュメント上にコントロールを追加する場所を指定する必要があります。 具体的な手順については、次のトピックを参照してください。  

-   [方法: ワークシートに ListObject コントロールを追加する](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [方法: ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [方法: ワークシートに Chart コントロールを追加する](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [方法: Word 文書にコンテンツ コントロールを追加する](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [方法: Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 ホスト コントロールについて詳しくは、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」をご覧ください。  

 ドキュメントを保存して閉じると、動的に作成したすべてのホスト コントロールはそれぞれイベントから切断され、データ バインディング機能も失われます。 ソリューションにコードを追加すれば、ドキュメントが再び開かれる時点でホスト コントロールを再作成するようにできます。 詳細については、「 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)」を参照してください。  

> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>、および <xref:Microsoft.Office.Tools.Word.XMLNodes>の各ホスト コントロールは、プログラムでドキュメントに追加することができないため、ヘルパー メソッドは用意されていません。  

##  <a name="WindowsForms"></a> Adding Windows Forms Controls to Documents  
 Windows フォーム コントロールをプログラムでドキュメントに追加する場合は、コントロールの場所とコントロールを一意に識別する名前を指定する必要があります。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] が、各コントロールのヘルパー メソッドを提供します。 これらのメソッドはオーバーロードされているため、コントロールの場所として範囲または特定の座標のいずれかを渡すことができます。  

 ドキュメントを保存して閉じると、動的に作成されたすべての Windows フォーム コントロールはドキュメントから削除されます。 ソリューションにコードを追加すれば、ドキュメントが再び開かれる時点でコントロールを再作成するようにできます。 VSTO アドインを使用して動的な Windows フォーム コントロールを作成した場合は、コントロールの ActiveX ラッパーがドキュメントに残されます。 詳細については、「 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)」を参照してください。  

> [!NOTE]  
>  Windows フォーム コントロールは、保護されているドキュメントにはプログラムで追加できません。 コントロールを追加するために、Word 文書または Excel ワークシートの保護をプログラムで解除する場合は、ドキュメントを閉じるときにコントロールの ActiveX ラッパーを削除するコードを追加で記述する必要があります。 コントロールの ActiveX ラッパーは、保護されたドキュメントから自動的には削除されません。  

### <a name="adding-custom-controls"></a>カスタム コントロールの追加  
 カスタム ユーザー コントロールなど、使用可能なヘルパー メソッドによってサポートされていない <xref:System.Windows.Forms.Control> を追加するには、次のメソッドを使用します。  

-   Excel では、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> オブジェクトの <xref:Microsoft.Office.Tools.Excel.ControlCollection> メソッドの 1 つを使用します。  

-   Word では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> オブジェクトの <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドの 1 つを使用します。  

 コントロールを追加するには、渡す、<xref:System.Windows.Forms.Control>コントロールは、場所、および AddControl メソッドにコントロールを一意に識別する名前。 AddControl メソッドは、コントロールがワークシートまたは文書とやり取りする方法を定義するオブジェクトを返します。 AddControl メソッドを返します、 <xref:Microsoft.Office.Tools.Excel.ControlSite> (for Excel)、または<xref:Microsoft.Office.Tools.Word.ControlSite>オブジェクト (Word)。  

 次のコード例は、 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> メソッドを使用して、ドキュメント レベルの Excel プロジェクトのワークシートにカスタム ユーザー コントロールを動的に追加する方法を示しています。 この例では、ユーザー コントロールの名前は `UserControl1`で、 <xref:Microsoft.Office.Interop.Excel.Range> の名前は `range1`です。 このコード例を使用するには、プロジェクトの `Sheet`*n* クラスから実行します。  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="using-members-of-custom-controls"></a>カスタム コントロールのメンバーを使用する  
 AddControl メソッドのいずれかを使用して、ワークシートまたは文書にコントロールを追加する、2 つの異なるコントロール オブジェクトがあるようになりました。  

-   カスタム コントロールを表す <xref:System.Windows.Forms.Control> 。  

-   ワークシートまたは文書に追加された後に、コントロールを表す ControlSite、OLEObject、または OLEControl オブジェクト。  

 これらのコントロールには、共有されているプロパティやメソッドが多数あります。 これらのメンバーには、適切なコントロールを介してアクセスすることが重要です。  

-   カスタム コントロールのみに属するメンバーにアクセスするには、 <xref:System.Windows.Forms.Control>を使用します。  

-   コントロールによって共有されているメンバーにアクセスするには、ControlSite、OLEObject、または OLEControl オブジェクトを使用します。  

 共有されているメンバーに <xref:System.Windows.Forms.Control>からアクセスすると、警告や通知なしに失敗したり、無効な結果が生成されたりすることがあります。 メソッドまたは必要なプロパティが使用可能な; がない限り、常に、ControlSite、OLEObject、または OLEControl オブジェクトのメソッドまたはプロパティを使用します。しかし、参照する必要がある、<xref:System.Windows.Forms.Control>です。  

 たとえば、両方、<xref:Microsoft.Office.Tools.Excel.ControlSite>クラスおよび<xref:System.Windows.Forms.Control>クラスには、最上位のプロパティが設定されています。 コントロールの上端からドキュメントの先頭までの間の距離を取得または設定するには、 <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> の <xref:Microsoft.Office.Tools.Excel.ControlSite>プロパティではなく、 <xref:System.Windows.Forms.Control.Top%2A> の <xref:System.Windows.Forms.Control>プロパティを使用してください。  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Office 文書で動的コントロールの永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [方法: ワークシートに ListObject コントロールを追加します。](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法: ワークシートに Chart コントロールを追加します。](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [方法: Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [方法 : Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [方法: Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
