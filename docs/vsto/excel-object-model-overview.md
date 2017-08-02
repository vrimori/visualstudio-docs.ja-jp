---
title: "Excel オブジェクト モデルの概要"
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
  - "Excel オブジェクト モデル"
  - "オブジェクト モデル [Visual Studio での Office 開発], Excel"
  - "オブジェクト モデル [Visual Studio での Office 開発], Office"
  - "オブジェクト [Visual Studio での Office 開発], Office オブジェクト モデル"
  - "Office オブジェクト モデル"
  - "Range オブジェクト"
  - "Workbook クラス"
  - "Worksheet オブジェクト"
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: 66
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 65
---
# Excel オブジェクト モデルの概要
  Microsoft Office Excel を使用するソリューションを開発するため、Excel オブジェクト モデルによって提供されるオブジェクトと対話することができます。  このトピックでは、特に重要なオブジェクトについて説明します。  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 オブジェクト モデルは、ユーザー インターフェイスに緊密に従います。   <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、アプリケーション全体を表し、それぞれの <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトには `Worksheet` オブジェクトのコレクションが含まれます。  つまり、セルを表す主要な概念は <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトになり、これにより個々のセルやセルのグループを使用できるようになります。  
  
 Visual Studio の Office プロジェクトは、Excel オブジェクト モデルだけでなく、Excel オブジェクト モデルの一部のオブジェクトを拡張する*ホスト項目*と*ホスト コントロール*を提供します。  ホスト項目とホスト コントロールは、これらが拡張する Excel オブジェクトと同様に動作しますが、これ以外にデータ バインド機能や他のイベントなどの追加機能もあります。  詳細については、「[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)」と「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 ここでは、Excel オブジェクト モデルの概念について簡単に説明します。  リソースについては、「[Excel オブジェクト モデル ドキュメントの使用](#ExcelOMDocumentation)」を参照して、全体の Excel オブジェクト モデルの詳細を入手してください。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連するビデオ デモについては、「[Excel 2007 アドインでイベント ハンドラーを使用する方法](http://go.microsoft.com/fwlink/?LinkID=130291)」および「[Excel で図形を使用してバブル チャートを作成する方法](http://go.microsoft.com/fwlink/?LinkID=130313)」を参照してください。  
  
## Excel プロジェクト内のオブジェクトへのアクセス  
 Excel で新しい VSTO アドイン プロジェクトを作成すると、Visual Studio によって ThisAddIn.vb または ThisAddIn.cs というコード ファイルが自動的に作成されます。   `Me.Application` または `this.Application` を使用して、アプリケーション オブジェクトにアクセスすることができます。  
  
 Excel で新しいドキュメント レベルのプロジェクトを作成する場合は、新しい Excel ブックまたは Excel テンプレート プロジェクトを作成するオプションがあります。  Visual Studio によって新しい Excel プロジェクトの次のコード ファイルがブックとテンプレートの両方のプロジェクトで自動的に作成されます。  
  
|Visual Basic|C\#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 プロジェクト内の `Globals` クラスを使用して、それぞれのクラスの外部から `ThisWorkbook`、`Sheet1`、`Sheet2`、または `Sheet3` にアクセスすることができます。  詳細については、「[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)」を参照してください。  次の例では、コードが `Sheet`*n* クラスまたは `ThisWorkbook` クラスのいずれかに配置されるかどうかに関係なく、`Sheet1` の <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> メソッドを呼び出します。  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#82)]  
  
 Excel ドキュメントのデータは高度に構造化されているため、オブジェクト モデルは階層的で単純です。  Excel では対話が可能な何百ものオブジェクトを提供していますが、最初にオブジェクト モデルを使い始めるときは、使用可能なオブジェクトの非常に小さなサブセットに重点を置くと良いでしょう。  このようなオブジェクトには次の 4 つがあります。  
  
-   アプリケーション  
  
-   ブック  
  
-   ワークシート  
  
-   範囲  
  
 Excel の作業の多くはこれら 4 つのオブジェクトとそのメンバーを中心に行われます。  
  
### アプリケーション オブジェクト  
 Excel の <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、Excel のアプリケーション自体を表します。  <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、実行中のアプリケーション、そのインスタンスに適用されるオプション、そのインスタンス内で開いている現在のユーザー オブジェクトに関する多くの情報を公開します。  
  
> [!NOTE]  
>  Excel の <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトの <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> プロパティを **false** に設定しないでください。  このプロパティを false に設定すると、ホスト コントロールのイベントを含む、すべてのイベントが Excel で発生しなくなります。  
  
### ブックのオブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトは、Excel アプリケーション内の 1 つのブックを表します。  
  
 Visual Studio の Office 開発ツールは、<xref:Microsoft.Office.Tools.Excel.Workbook> 型を提供することにより、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトを拡張します。  この型により、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトのすべての機能にアクセスできるようになります。  詳細については、「[Workbook ホスト項目](../vsto/workbook-host-item.md)」を参照してください。  
  
### ワークシート オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトは <xref:Microsoft.Office.Interop.Excel.Worksheets> コレクションのメンバーです。  <xref:Microsoft.Office.Interop.Excel.Worksheet> のプロパティ、メソッド、およびイベントの多くは、<xref:Microsoft.Office.Interop.Excel.Application> または <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトによって提供されるメンバーと同一か類似しています。  
  
 Excel は、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトのプロパティとして <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを提供します。  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの各メンバーは、<xref:Microsoft.Office.Interop.Excel.Worksheet> または <xref:Microsoft.Office.Interop.Excel.Chart> オブジェクトのどちらかです。  
  
 Visual Studio の Office 開発ツールは、<xref:Microsoft.Office.Tools.Excel.Worksheet> 型を提供することにより、<xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトを拡張します。  この型は <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトのすべての機能にアクセスできるだけでなく、マネージ コントロールをホストし、新しいイベントを処理する機能などの新機能にもアクセスできます。  詳細については、「[Worksheet ホスト項目](../vsto/worksheet-host-item.md)」を参照してください。  
  
### 範囲オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトは、Excel アプリケーション内で特に使用されるオブジェクトです。  Excel 内で任意の領域を操作するには、その領域を <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトとして表し、その範囲のメソッドとプロパティを作業する必要があります。  <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトは、セル、行、列、セルの 1 つ以上のブロックを含むセルの選択を表します。連続する場合もしない場合もあり、セルのグループが複数のシートにわたっている場合もあります。  
  
 Visual Studio は <xref:Microsoft.Office.Tools.Excel.NamedRange> および <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 型を提供することで <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトを拡張します。  これらの型は <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトとほぼ同じ機能を含むだけでなく、データ バインド機能や新しいイベントなどの新機能も含んでいます。  詳細については、「[NamedRange コントロール](../vsto/namedrange-control.md)」と「[XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)」を参照してください。  
  
##  <a name="ExcelOMDocumentation"></a> Excel オブジェクト モデル ドキュメントの使用  
 Excel オブジェクト モデルに関する詳細については、Excel プライマリ相互運用機能アセンブリ \(PIA\) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### プライマリ相互運用機能アセンブリのリファレンス  
 Excel PIA のリファレンス ドキュメントは、Excel のプライマリ相互運用機能アセンブリの種類について説明しています。  このドキュメントは、「[Excel 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)」から入手できます。  
  
 PIA のクラスとインターフェイスの違い、PIA 内でのイベントの実装方法など、Excel PIA の設計に関する詳細については、「[Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)」を参照してください。  
  
### VBA オブジェクト モデルのリファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications \(VBA\) コードに公開される Excel オブジェクト モデルについて説明しています。  詳細については、「[オブジェクト モデル リファレンス \(Excel 2013 開発者用リファレンス\)](http://go.microsoft.com/fwlink/?LinkId=199768)」を参照してください。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Excel PIA の型とメンバーに対応します。  たとえば、VBA オブジェクト モデルのリファレンス内の Worksheet オブジェクトは、Excel PIA の <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトに対応します。  VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Excel プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C\# に変換する必要があります。  
  
### 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[Excel ソリューション](../vsto/excel-solutions.md)|Microsoft Office Excel でドキュメント レベルのカスタマイズと VSTO アドインを作成する方法について説明します。|  
|[範囲の使用](../vsto/working-with-ranges.md)|範囲を使用して一般的なタスクを実行する方法を示す例を提供します。|  
|[ワークシートの操作](../vsto/working-with-worksheets.md)|ワークシートを使用して一般的なタスクを実行する方法を示す例を提供します。|  
|[ブックの操作](../vsto/working-with-workbooks.md)|ブックを使用して一般的なタスクを実行する方法を示す例を提供します。|  
  
  