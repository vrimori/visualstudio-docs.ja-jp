---
title: "実行時に Word 文書と VSTO アドイン内の Excel ブックを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5cd29d7de596704087eb1326791e4fc9df9921a6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張
  VSTO アドインを利用すれば、Word 文書と Excel ブックを次のようにカスタマイズできます。  
  
-   開いている文書またはブックに管理されているコントロールを追加します。  
  
-   Excel ワークシートの既存のリスト オブジェクトを、イベントを公開し、Windows フォーム データ バインディング モデルでデータにバインディングできる拡張 <xref:Microsoft.Office.Tools.Excel.ListObject> に変換します。  
  
-   特定の文書、ブック、ワークシートに対して Word と Excel が公開するアプリケーションレベル イベントにアクセスします。  
  
 この機能を使用するには、文書またはブックを拡張するオブジェクトを実行時に生成します。  
  
 **対象:** このトピックの情報は Excel と Word の VSTO アドインのプロジェクトに適用されます。 詳細については、「 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
## <a name="generating-extended-objects-in-vsto-add-ins"></a>VSTO アドインで拡張オブジェクトを生成する  
 *拡張オブジェクト* は Word または Excel オブジェクト モデルにネイティブで存在するオブジェクト ( *ネイティブ Office オブジェクト*) に機能を追加する Visual Studio Tools for Office Runtime が提供する種類のインスタンスです。 Word または Excel オブジェクトの拡張オブジェクトを生成するには、GetVstoObject メソッドを使用します。 最初に指定した Word または Excel のオブジェクトの GetVstoObject メソッドを呼び出したとき、指定したオブジェクトを拡張する新しいオブジェクトを返します。 このメソッドを呼び出し、同じ Word または Excel を指定するたびに、同じ拡張オブジェクトが返されます。  
  
 拡張オブジェクトの種類にはネイティブ Office オブジェクトの種類と同じ名前が与えられますが、この種類は <xref:Microsoft.Office.Tools.Excel> または <xref:Microsoft.Office.Tools.Word> 名前空間で定義されます。 たとえば、拡張する GetVstoObject メソッドを呼び出す場合、<xref:Microsoft.Office.Interop.Word.Document>オブジェクトをメソッドが返されます、<xref:Microsoft.Office.Tools.Word.Document>オブジェクト。  
  
 GetVstoObject メソッドは主に VSTO アドイン プロジェクトで使用するためのものです。 ドキュメントレベル プロジェクトでこれらのメソッドを使用することもできますが、動作が異なり、用途が少なくなります。  
  
 特定のネイティブ Office オブジェクトに対して拡張オブジェクトが既に生成されているかどうかを確認するのには、HasVstoObject メソッドを使用します。 詳細については、「 [Office オブジェクトが拡張されているかどうかを判断する](#HasVstoObject)」を参照してください。  
  
### <a name="generating-host-items"></a>ホスト項目を生成する  
 ドキュメント レベルのオブジェクトを拡張、getvstoobject メソッドを使用する場合 (つまり、 <xref:Microsoft.Office.Interop.Excel.Workbook>、 <xref:Microsoft.Office.Interop.Excel.Worksheet>、または<xref:Microsoft.Office.Interop.Word.Document>)、返されるオブジェクトが呼び出されると、*ホスト項目*です。 ホスト項目は、他の拡張されたオブジェクトやコントロールなど、他のオブジェクトを含めることができる種類です。 Word または Excel プライマリ相互運用機能アセンブリの対応する種類と似ていますが、機能が多くなっています。 ホスト項目の詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 ホスト項目を生成したら、それを利用して管理されているコントロールを文書、ブック、ワークシートに追加できます。 詳細については、「 [文書とワークシートに管理されているコントロールを追加する](#AddControls)」を参照してください。  
  
##### <a name="to-generate-a-host-item-for-a-word-document"></a>Word 文書のホスト項目を生成するには  
  
-   次のコード例はアクティブな文書のホスト項目を生成する方法を示しています。  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Excel ブックのホスト項目を生成するには  
  
-   次のコード例はアクティブなブックのホスト項目を生成する方法を示しています。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Excel ワークシートのホスト項目を生成するには  
  
-   次のコード例はプロジェクトのアクティブなワークシートのホスト項目を生成する方法を示しています。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generating-listobject-host-controls"></a>ListObject ホスト コントロールを生成する  
 GetVstoObject メソッドを使用して拡張するときに、 <xref:Microsoft.Office.Interop.Excel.ListObject>、メソッドを返します、<xref:Microsoft.Office.Tools.Excel.ListObject>です。 <xref:Microsoft.Office.Tools.Excel.ListObject> は元の <xref:Microsoft.Office.Interop.Excel.ListObject>のすべての機能を備えており、さらに、Windows フォーム データ バインディング モデルを使用してデータにバインドする機能などの機能も追加されています。 詳細については、「 [ListObject Control](../vsto/listobject-control.md)」を参照してください。  
  
##### <a name="to-generate-a-host-control-for-a-listobject"></a>ListObject のホスト コントロールを生成するには  
  
-   次のコード例はプロジェクトのアクティブなワークシートの最初の <xref:Microsoft.Office.Tools.Excel.ListObject> に対して <xref:Microsoft.Office.Interop.Excel.ListObject> を生成する方法を示しています。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
##  <a name="AddControls"></a> 文書とワークシートに管理されているコントロールを追加する  
 <xref:Microsoft.Office.Tools.Word.Document> または <xref:Microsoft.Office.Tools.Excel.Worksheet>を生成したら、これらの拡張オブジェクトが表す文書またはワークシートにコントロールを追加できます。 これを行うには、コントロール プロパティを使用して、<xref:Microsoft.Office.Tools.Word.Document>または<xref:Microsoft.Office.Tools.Excel.Worksheet>です。 詳細については、「 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 Windows フォーム コントロールまたは *ホスト コントロール*を追加できます。 ホスト コントロールは [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] により提供されるコントロールであり、Word または Excel プライマリ相互運用機能アセンブリのそれに対応するコントロールをラップします。 ホスト コントロールは基礎となるネイティブ Office オブジェクトのすべての動作を見せますが、さらに、イベントを発生させ、Windows フォーム データ バインディング モデルを利用してデータにバインディングできます。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
> [!NOTE]  
>  VSTO アドインを利用し、 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールをワークシートに、 <xref:Microsoft.Office.Tools.Word.XMLNode> または <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールを文書に追加することはできません。 これらのホスト コントロールをプログラミングで追加することはできません。 詳細については、「 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
### <a name="persisting-and-removing-controls"></a>コントロールの保持と削除  
 管理されているコントロールを文書またはワークシートに追加するとき、文書を保存し、閉じても、コントロールは保持されません。 基礎となるネイティブ Office オブジェクトだけが残るようにすべてのホスト コントロールが削除されます。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:Microsoft.Office.Interop.Excel.ListObject>になります。 すべての Windows フォーム コントロールも削除されますが、ActiveX ラッパーは文書に残ります。 コントロールを消去するか、文書を次回開いたときにコントロールを再作成するには、VSTO アドインにコードを追加する必要があります。 詳細については、「 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)」を参照してください。  
  
## <a name="accessing-application-level-events-on-documents-and-workbooks"></a>文書とブックでアプリケーションレベル イベントにアクセスする  
 ネイティブの Word または Excel オブジェクト モデルの一部の文書、ブック、ワークシート イベントはアプリケーション レベルでのみ発生します。 たとえば、 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントは文書を Word で開いたときに発生しますが、このイベントは <xref:Microsoft.Office.Interop.Word.Application> クラスではなく、 <xref:Microsoft.Office.Interop.Word.Document> クラスに定義されています。  
  
 VSTO アドインでネイティブ Office オブジェクトを使用するとき、これらのアプリケーションレベル イベントを処理し、イベントを発生された文書が自分でカスタマイズした文書であるかどうかを判断する追加コードを記述する必要があります。 ホスト項目は文書レベルでこれらのイベントを提供します。そのため、特定の文書のイベントを簡単に処理できます。 ホスト項目を生成し、そのホスト項目のイベントを処理できます。  
  
### <a name="example-that-uses-native-word-objects"></a>ネイティブ Word オブジェクトを使用する例  
 次のコード例は Word 文書のアプリケーションレベル イベントの処理方法を示しています。 `CreateDocument` メソッドは新しい文書を作成し、その文書が保存されないようにする <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベント ハンドラーを定義します。 これは <xref:Microsoft.Office.Interop.Word.Application> オブジェクトに発生したアプリケーションレベル イベントであるため、イベント ハンドラーは `Doc` パラメーターと `document1` オブジェクトを比較し、 `document1` が保存された文書を表すかどうかを判断します。  
  
 [!code-vb[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>ホスト項目を使用する例  
 次のコード例では、 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> ホスト項目の <xref:Microsoft.Office.Tools.Word.Document> イベントを処理することでこのプロセスを簡略化しています。 これらの例の `CreateDocument2` メソッドは <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを拡張する `document2` を生成し、文書が保存されないようにする <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> イベント ハンドラーを定義します。 このイベント ハンドラーは `document2` が保存されるときにのみ呼び出されるため、イベント ハンドラーは保存された文書を確認する追加の作業なしで保存操作を取り消すことができます。  
  
 次のコード例はこの作業を示しています。  
  
 [!code-vb[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Office オブジェクトが拡張されているかどうかを判断する  
 特定のネイティブ Office オブジェクトに対して拡張オブジェクトが既に生成されているかどうかを確認するのには、HasVstoObject メソッドを使用します。 拡張オブジェクトが既に生成されている場合、このメソッドは **true** を返します。生成されていない場合、 **false**を返します。  
  
 Globals.Factory.HasVstoMethod メソッドを使用します。 拡張オブジェクトに対してテストするネイティブの Word または Excel オブジェクト ( <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Excel.Worksheet>など) を渡します。  
  
 HasVstoObject メソッドは、指定した Office オブジェクトに拡張オブジェクトがある場合にのみ、コードを実行するときに役立ちます。 処理する Word VSTO アドインがある場合など、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>する前に文書から管理されているコントロールを削除するイベントの保存、HasVstoObject メソッドを使用するを文書が拡張されているかどうかを判断します。 文書が拡張されていない場合、管理されているコントロールを追加できません。そのため、イベント ハンドラーは文書のコントロールを消去せずに戻ります。  
  
## <a name="see-also"></a>参照  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)  
  
  