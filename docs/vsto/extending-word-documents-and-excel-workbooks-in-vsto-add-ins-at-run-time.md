---
title: "VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張"
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
  - "GetVstoObject メソッド"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、追加 (ドキュメントにコントロールを)"
  - "ホスト項目 [Visual Studio での Office 開発]、作成 (実行時にアドインで)"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、拡張 (Word 文書を)"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、拡張 (Excel ブックを)"
  - "コントロール [Visual Studio での Office 開発]、追加 (実行時に)"
  - "HasVstoObject メソッド"
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張
  VSTO アドインを利用すれば、Word 文書と Excel ブックを次のようにカスタマイズできます。  
  
-   開いている文書またはブックに管理されているコントロールを追加します。  
  
-   Excel ワークシートの既存のリスト オブジェクトを、イベントを公開し、Windows フォーム データ バインディング モデルでデータにバインディングできる拡張 <xref:Microsoft.Office.Tools.Excel.ListObject> に変換します。  
  
-   特定の文書、ブック、ワークシートに対して Word と Excel が公開するアプリケーションレベル イベントにアクセスします。  
  
 この機能を使用するには、文書またはブックを拡張するオブジェクトを実行時に生成します。  
  
 **対象:** このトピックの情報は Excel と Word の VSTO アドインのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
## VSTO アドインで拡張オブジェクトを生成する  
 *拡張オブジェクト*は Word または Excel オブジェクト モデルにネイティブで存在するオブジェクト \(*ネイティブ Office オブジェクト*\) に機能を追加する Visual Studio Tools for Office Runtime が提供する種類のインスタンスです。 Word または Excel オブジェクトの拡張オブジェクトを生成するにはGetVstoObject メソッドを使用します。 指定した Word または Excel オブジェクトに対して GetVstoObject メソッドを初めて呼び出すと、指定したオブジェクトを拡張する新しいオブジェクトが返されます。 このメソッドを呼び出し、同じ Word または Excel を指定するたびに、同じ拡張オブジェクトが返されます。  
  
 拡張オブジェクトの種類にはネイティブ Office オブジェクトの種類と同じ名前が与えられますが、この種類は <xref:Microsoft.Office.Tools.Excel> または <xref:Microsoft.Office.Tools.Word> 名前空間で定義されます。 たとえば、GetVstoObject メソッドを呼び出し、<xref:Microsoft.Office.Interop.Word.Document> オブジェクトを拡張した場合、このメソッドは <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを返します。  
  
 GetVstoObject メソッドは主に VSTO アドイン プロジェクトで使用するためのものです。 ドキュメントレベル プロジェクトでこれらのメソッドを使用することもできますが、動作が異なり、用途が少なくなります。  
  
 特定のネイティブ Office オブジェクトに対して拡張オブジェクトが既に生成されているかどうかを確認するには、HasVstoObject メソッドを使用します。 詳細については、「[Office オブジェクトが拡張されているかどうかを判断する](#HasVstoObject)」を参照してください。  
  
### ホスト項目を生成する  
 GetVstoObject を利用してドキュメントレベル オブジェクト \(つまり、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet>、<xref:Microsoft.Office.Interop.Word.Document>\) を拡張するとき、返されるオブジェクトは「*ホスト項目*」と呼ばれます。 ホスト項目は、他の拡張されたオブジェクトやコントロールなど、他のオブジェクトを含めることができる種類です。 Word または Excel プライマリ相互運用機能アセンブリの対応する種類と似ていますが、機能が多くなっています。 ホスト項目の詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 ホスト項目を生成したら、それを利用して管理されているコントロールを文書、ブック、ワークシートに追加できます。 詳細については、「[文書とワークシートに管理されているコントロールを追加する](#AddControls)」を参照してください。  
  
##### Word 文書のホスト項目を生成するには  
  
-   次のコード例はアクティブな文書のホスト項目を生成する方法を示しています。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_WordAddInDynamicControls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#8)]  
  
##### Excel ブックのホスト項目を生成するには  
  
-   次のコード例はアクティブなブックのホスト項目を生成する方法を示しています。  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
##### Excel ワークシートのホスト項目を生成するには  
  
-   次のコード例はプロジェクトのアクティブなワークシートのホスト項目を生成する方法を示しています。  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
### ListObject ホスト コントロールを生成する  
 GetVstoObject メソッドを利用して <xref:Microsoft.Office.Interop.Excel.ListObject> を拡張すると、このメソッドは <xref:Microsoft.Office.Tools.Excel.ListObject> を返します。<xref:Microsoft.Office.Tools.Excel.ListObject> は元の <xref:Microsoft.Office.Interop.Excel.ListObject> のすべての機能を備えており、さらに、Windows フォーム データ バインディング モデルを使用してデータにバインドする機能などの機能も追加されています。 詳細については、「[ListObject コントロール](../vsto/listobject-control.md)」を参照してください。  
  
##### ListObject のホスト コントロールを生成するには  
  
-   次のコード例はプロジェクトのアクティブなワークシートの最初の <xref:Microsoft.Office.Interop.Excel.ListObject> に対して <xref:Microsoft.Office.Tools.Excel.ListObject> を生成する方法を示しています。  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
##  <a name="AddControls"></a> 文書とワークシートに管理されているコントロールを追加する  
 <xref:Microsoft.Office.Tools.Word.Document> または <xref:Microsoft.Office.Tools.Excel.Worksheet> を生成したら、これらの拡張オブジェクトが表す文書またはワークシートにコントロールを追加できます。 これを行うには、<xref:Microsoft.Office.Tools.Word.Document> または <xref:Microsoft.Office.Tools.Excel.Worksheet> の Controls プロパティを使用します。 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 Windows フォーム コントロールまたは*ホスト コントロール*を追加できます。 ホスト コントロールは [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] により提供されるコントロールであり、Word または Excel プライマリ相互運用機能アセンブリのそれに対応するコントロールをラップします。 ホスト コントロールは基礎となるネイティブ Office オブジェクトのすべての動作を見せますが、さらに、イベントを発生させ、Windows フォーム データ バインディング モデルを利用してデータにバインディングできます。 詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
> [!NOTE]  
>  VSTO アドインを利用し、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールをワークシートに、<xref:Microsoft.Office.Tools.Word.XMLNode> または <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールを文書に追加することはできません。 これらのホスト コントロールをプログラミングで追加することはできません。 詳細については、「[ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
### コントロールの保持と削除  
 管理されているコントロールを文書またはワークシートに追加するとき、文書を保存し、閉じても、コントロールは保持されません。 基礎となるネイティブ Office オブジェクトだけが残るようにすべてのホスト コントロールが削除されます。 たとえば、<xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:Microsoft.Office.Interop.Excel.ListObject> になります。 すべての Windows フォーム コントロールも削除されますが、ActiveX ラッパーは文書に残ります。 コントロールを消去するか、文書を次回開いたときにコントロールを再作成するには、VSTO アドインにコードを追加する必要があります。 詳細については、「[Office ドキュメントでのダイナミック コントロールの永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)」を参照してください。  
  
## 文書とブックでアプリケーションレベル イベントにアクセスする  
 ネイティブの Word または Excel オブジェクト モデルの一部の文書、ブック、ワークシート イベントはアプリケーション レベルでのみ発生します。 たとえば、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントは文書を Word で開いたときに発生しますが、このイベントは <xref:Microsoft.Office.Interop.Word.Document> クラスではなく、<xref:Microsoft.Office.Interop.Word.Application> クラスに定義されています。  
  
 VSTO アドインでネイティブ Office オブジェクトを使用するとき、これらのアプリケーションレベル イベントを処理し、イベントを発生された文書が自分でカスタマイズした文書であるかどうかを判断する追加コードを記述する必要があります。 ホスト項目は文書レベルでこれらのイベントを提供します。そのため、特定の文書のイベントを簡単に処理できます。 ホスト項目を生成し、そのホスト項目のイベントを処理できます。  
  
### ネイティブ Word オブジェクトを使用する例  
 次のコード例は Word 文書のアプリケーションレベル イベントの処理方法を示しています。`CreateDocument` メソッドは新しい文書を作成し、その文書が保存されないようにする <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベント ハンドラーを定義します。 これは <xref:Microsoft.Office.Interop.Word.Application> オブジェクトに発生したアプリケーションレベル イベントであるため、イベント ハンドラーは `Doc` パラメーターと `document1` オブジェクトを比較し、`document1` が保存された文書を表すかどうかを判断します。  
  
 [!code-csharp[Trin_WordAddInDynamicControls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#12)]
 [!code-vb[Trin_WordAddInDynamicControls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#12)]  
  
### ホスト項目を使用する例  
 次のコード例では、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目の <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> イベントを処理することでこのプロセスを簡略化しています。 これらの例の `CreateDocument2` メソッドは `document2` オブジェクトを拡張する <xref:Microsoft.Office.Tools.Word.Document> を生成し、文書が保存されないようにする <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> イベント ハンドラーを定義します。 このイベント ハンドラーは `document2` が保存されるときにのみ呼び出されるため、イベント ハンドラーは保存された文書を確認する追加の作業なしで保存操作を取り消すことができます。  
  
 次のコード例はこの作業を示しています。  
  
 [!code-csharp[Trin_WordAddInDynamicControls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#13)]
 [!code-vb[Trin_WordAddInDynamicControls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#13)]  
  
##  <a name="HasVstoObject"></a> Office オブジェクトが拡張されているかどうかを判断する  
 特定のネイティブ Office オブジェクトに対して拡張オブジェクトが既に生成されているかどうかを確認するには、HasVstoObject メソッドを使用します。 拡張オブジェクトが既に生成されている場合、このメソッドは **true** を返します。生成されていない場合、**false** を返します。  
  
 Globals.Factory.HasVstoMethod メソッドを使用します。 拡張オブジェクトに対してテストするネイティブの Word または Excel オブジェクト \(<xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Excel.Worksheet> など\) を渡します。  
  
 HasVstoObject メソッドは、指定した Office オブジェクトに拡張オブジェクトがある場合にのみ、コードの実行で便利です。 たとえば、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントを処理し、文書の保存前に文書から管理されているコントロールを削除する Word VSTO アドインがある場合、HasVstoObject メソッドを使用し、文書が拡張されているかどうかを判断できます。 文書が拡張されていない場合、管理されているコントロールを追加できません。そのため、イベント ハンドラーは文書のコントロールを消去せずに戻ります。  
  
## 参照  
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)  
  
  