---
title: Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8c3527070c1934c723b6038c93347f1a78ac948a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864879"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>Word 文書や実行時に VSTO のアドインの Excel ブックを拡張します。
  VSTO アドインを利用すれば、Word 文書と Excel ブックを次のようにカスタマイズできます。  
  
- 開いている文書またはブックに管理されているコントロールを追加します。  
  
- Excel ワークシートの既存のリスト オブジェクトを、イベントを公開し、Windows フォーム データ バインディング モデルでデータにバインディングできる拡張 <xref:Microsoft.Office.Tools.Excel.ListObject> に変換します。  
  
- 特定の文書、ブック、ワークシートに対して Word と Excel が公開するアプリケーションレベル イベントにアクセスします。  
  
  この機能を使用するには、ドキュメントまたはブックを拡張する実行時にオブジェクトを生成します。  
  
  **適用対象します。** この記事の情報は、次のアプリケーション用の VSTO アドイン プロジェクトに適用されます。Excel および Word です。 詳細については、次を参照してください。 [Office アプリケーションおよびプロジェクトの種類で使用できる機能](../vsto/features-available-by-office-application-and-project-type.md)します。  
  
## <a name="generate-extended-objects-in-vsto-add-ins"></a>VSTO アドインで拡張されたオブジェクトを生成します。  
 *拡張オブジェクト* は Word または Excel オブジェクト モデルにネイティブで存在するオブジェクト ( *ネイティブ Office オブジェクト*) に機能を追加する Visual Studio Tools for Office Runtime が提供する種類のインスタンスです。 Word または Excel オブジェクトの拡張オブジェクトを生成するには`GetVstoObject` メソッドを使用します。 最初に呼び出したとき、`GetVstoObject`メソッドを指定した Word または Excel のオブジェクトを指定したオブジェクトを拡張する新しいオブジェクトが返されます。 このメソッドを呼び出し、同じ Word または Excel を指定するたびに、同じ拡張オブジェクトが返されます。  
  
 拡張オブジェクトの種類にはネイティブ Office オブジェクトの種類と同じ名前が与えられますが、この種類は <xref:Microsoft.Office.Tools.Excel> または <xref:Microsoft.Office.Tools.Word> 名前空間で定義されます。 たとえば、`GetVstoObject` メソッドを呼び出し、<xref:Microsoft.Office.Interop.Word.Document> オブジェクトを拡張した場合、このメソッドは <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを返します。  
  
 `GetVstoObject` メソッドは主に VSTO アドイン プロジェクトで使用するためのものです。 ドキュメントレベル プロジェクトでこれらのメソッドを使用することもできますが、動作が異なり、用途が少なくなります。  
  
 特定のネイティブ Office オブジェクトに対して拡張オブジェクトが既に生成されているかどうかを確認するには、`HasVstoObject` メソッドを使用します。 詳細については、次を参照してください。 [Office オブジェクトが拡張されているかどうかを判断](#HasVstoObject)します。  
  
### <a name="generate-host-items"></a>ホスト項目を生成します。  
 使用する場合、`GetVstoObject`ドキュメント レベルのオブジェクトを拡張 (つまり、 <xref:Microsoft.Office.Interop.Excel.Workbook>、 <xref:Microsoft.Office.Interop.Excel.Worksheet>、または<xref:Microsoft.Office.Interop.Word.Document>)、返されたオブジェクトが呼び出されます、*ホスト項目*。 ホスト項目は、他の拡張されたオブジェクトやコントロールなど、他のオブジェクトを含めることができる種類です。 Word または Excel プライマリ相互運用機能アセンブリの対応する種類と似ていますが、機能が多くなっています。 ホスト項目の詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。  
  
 ホスト項目を生成したら、それを利用して管理されているコントロールを文書、ブック、ワークシートに追加できます。 詳細については、次を参照してください。[マネージ文書やワークシートにコントロールを追加](#AddControls)します。  
  
#### <a name="to-generate-a-host-item-for-a-word-document"></a>Word 文書のホスト項目を生成するには  
  
-   次のコード例はアクティブな文書のホスト項目を生成する方法を示しています。  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Excel ブックのホスト項目を生成するには  
  
-   次のコード例はアクティブなブックのホスト項目を生成する方法を示しています。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Excel ワークシートのホスト項目を生成するには  
  
-   次のコード例はプロジェクトのアクティブなワークシートのホスト項目を生成する方法を示しています。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generate-listobject-host-controls"></a>ListObject ホスト コントロールを生成します。  
 `GetVstoObject` メソッドを利用して <xref:Microsoft.Office.Interop.Excel.ListObject> を拡張すると、このメソッドは <xref:Microsoft.Office.Tools.Excel.ListObject> を返します。 <xref:Microsoft.Office.Tools.Excel.ListObject>が元の機能をすべて<xref:Microsoft.Office.Interop.Excel.ListObject>します。 追加の機能を持つまた、Windows フォーム データ バインディング モデルを使用してデータにバインドできます。 詳細については、次を参照してください。 [ListObject コントロール](../vsto/listobject-control.md)します。  
  
#### <a name="to-generate-a-host-control-for-a-listobject"></a>ListObject のホスト コントロールを生成するには  
  
-   次のコード例はプロジェクトのアクティブなワークシートの最初の <xref:Microsoft.Office.Tools.Excel.ListObject> に対して <xref:Microsoft.Office.Interop.Excel.ListObject> を生成する方法を示しています。  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
###  <a name="AddControls"></a> 文書やワークシートにマネージ コントロールを追加します。  
 <xref:Microsoft.Office.Tools.Word.Document> または <xref:Microsoft.Office.Tools.Excel.Worksheet>を生成したら、これらの拡張オブジェクトが表す文書またはワークシートにコントロールを追加できます。 コントロールを追加するには、使用、`Controls`のプロパティ、<xref:Microsoft.Office.Tools.Word.Document>または<xref:Microsoft.Office.Tools.Excel.Worksheet>します。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
 Windows フォーム コントロールまたは *ホスト コントロール*を追加できます。 ホスト コントロールは [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] により提供されるコントロールであり、Word または Excel プライマリ相互運用機能アセンブリのそれに対応するコントロールをラップします。 ホスト コントロールは、すべての基になるネイティブ Office オブジェクトの動作を公開します。 イベントを発生させ、Windows フォーム データ バインディング モデルを使用してデータにバインドできます。 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。  
  
> [!NOTE]  
>  VSTO アドインを利用し、 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールをワークシートに、 <xref:Microsoft.Office.Tools.Word.XMLNode> または <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールを文書に追加することはできません。 これらのホスト コントロールをプログラミングで追加することはできません。 詳細については、次を参照してください。[ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)します。  
  
### <a name="persist-and-remove-controls"></a>永続化し、コントロールを削除  
 管理されているコントロールを文書またはワークシートに追加するとき、文書を保存し、閉じても、コントロールは保持されません。 基礎となるネイティブ Office オブジェクトだけが残るようにすべてのホスト コントロールが削除されます。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:Microsoft.Office.Interop.Excel.ListObject>になります。 すべての Windows フォーム コントロールも削除されますが、ActiveX ラッパーは文書に残ります。 コントロールを消去するか、文書を次回開いたときにコントロールを再作成するには、VSTO アドインにコードを追加する必要があります。 詳細については、次を参照してください。 [Office ドキュメントでのダイナミック コントロールを永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)します。  
  
## <a name="access-application-level-events-on-documents-and-workbooks"></a>文書やブックのアクセスのアプリケーション レベルのイベント  
 ネイティブの Word または Excel オブジェクト モデルの一部の文書、ブック、ワークシート イベントはアプリケーション レベルでのみ発生します。 たとえば、 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントは文書を Word で開いたときに発生しますが、このイベントは <xref:Microsoft.Office.Interop.Word.Application> クラスではなく、 <xref:Microsoft.Office.Interop.Word.Document> クラスに定義されています。  
  
 VSTO アドインでネイティブ Office オブジェクトを使用するとき、これらのアプリケーションレベル イベントを処理し、イベントを発生された文書が自分でカスタマイズした文書であるかどうかを判断する追加コードを記述する必要があります。 ホスト項目は文書レベルでこれらのイベントを提供します。そのため、特定の文書のイベントを簡単に処理できます。 ホスト項目を生成し、そのホスト項目のイベントを処理できます。  
  
### <a name="example-that-uses-native-word-objects"></a>ネイティブな Word オブジェクトを使用する例  
 次のコード例は Word 文書のアプリケーションレベル イベントの処理方法を示しています。 `CreateDocument` メソッドは新しい文書を作成し、その文書が保存されないようにする <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベント ハンドラーを定義します。 イベントは、アプリケーション レベルのイベントの発生する、<xref:Microsoft.Office.Interop.Word.Application>オブジェクト、およびイベント ハンドラーを比較する必要があります、`Doc`パラメーター、`document1`オブジェクトかどうかを`document1`保存されたドキュメントを表します。  
  
 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>ホスト項目を使用する例  
 次のコード例では、 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> ホスト項目の <xref:Microsoft.Office.Tools.Word.Document> イベントを処理することでこのプロセスを簡略化しています。 `CreateDocument2`メソッドはこれらの例では、生成、<xref:Microsoft.Office.Tools.Word.Document>まで、`document2`オブジェクト、し、定義、<xref:Microsoft.Office.Tools.Word.Document.BeforeSave>ドキュメントが保存されるようにするイベント ハンドラー。 イベント ハンドラーは場合にのみと呼ばれる`document2`は保存され、保存を取り消すことができます保存された文書を確認する追加の作業を実行しなくても動作します。  
  
 次のコード例はこの作業を示しています。  
  
 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Office オブジェクトが拡張されているかどうかを判断します。  
 特定のネイティブ Office オブジェクトに対して拡張オブジェクトが既に生成されているかどうかを確認するには、`HasVstoObject` メソッドを使用します。 このメソッドが戻る**true**拡張オブジェクトが既に生成されている場合。  
  
 `Globals.Factory.HasVstoMethod` メソッドを使用します。 拡張オブジェクトに対してテストするネイティブの Word または Excel オブジェクト ( <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Excel.Worksheet>など) を渡します。  
  
 `HasVstoObject` メソッドは、指定した Office オブジェクトに拡張オブジェクトがある場合にのみ、コードの実行で便利です。 処理する Word VSTO アドインがある場合など、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>イベントが保存されるまで、マネージ コントロールをドキュメントから削除を使用して、`HasVstoObject`文書が拡張されているかどうかを判断するメソッド。 文書が拡張されていない場合は、コントロール、管理があることはできませんし、イベント ハンドラーがドキュメント上のコントロールをクリーンアップしようとしないで返すことができます。  
  
## <a name="see-also"></a>関連項目  
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)  
