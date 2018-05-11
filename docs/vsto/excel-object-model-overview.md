---
title: Excel オブジェクト モデルの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b700d3834cf432ff9af2ec17e1daa3011763cac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="excel-object-model-overview"></a>Excel Object Model Overview
  Microsoft Office Excel を使用するソリューションを開発するため、Excel オブジェクト モデルによって提供されるオブジェクトと対話することができます。 このトピックでは、特に重要なオブジェクトについて説明します。  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 オブジェクト モデルは、ユーザー インターフェイスに緊密に従います。 <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、アプリケーション全体を表し、それぞれの <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトには `Worksheet` オブジェクトのコレクションが含まれます。 つまり、セルを表す主要な概念は <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトになり、これにより個々のセルやセルのグループを使用できるようになります。  
  
 Visual Studio での Office プロジェクトを提供する Excel オブジェクト モデルだけでなく*ホスト項目*と*ホスト コントロール*Excel オブジェクト モデルの一部のオブジェクトを拡張します。 ホスト項目とホスト コントロールは、これらが拡張する Excel オブジェクトと同様に動作しますが、これ以外にデータ バインディング機能や他のイベントなどの追加機能もあります。 詳細については、次を参照してください。[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)と[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)です。  
  
 ここでは、Excel オブジェクト モデルの概念について簡単に説明します。 リソースについては、全体の Excel オブジェクト モデルの詳細についてここで、次を参照してください。 [Excel オブジェクト モデルのドキュメントを使用して](#ExcelOMDocumentation)です。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[方法は i: を使用してイベント ハンドラーで、Excel 2007 アドイン?](http://go.microsoft.com/fwlink/?LinkID=130291)、および[方法は図形を使用してバブル チャートを作成するには。excel しますか](http://go.microsoft.com/fwlink/?LinkID=130313)。  
  
## <a name="accessing-objects-in-an-excel-project"></a>Excel プロジェクト内のオブジェクトへのアクセス  
 Excel で新しい VSTO アドイン プロジェクトを作成すると、Visual Studio によって ThisAddIn.vb または ThisAddIn.cs というコード ファイルが自動的に作成されます。 `Me.Application` または `this.Application` を使用して、アプリケーション オブジェクトにアクセスすることができます。  
  
 Excel で新しいドキュメント レベルのプロジェクトを作成する場合は、新しい Excel ブックまたは Excel テンプレート プロジェクトを作成するオプションがあります。 Visual Studio によって新しい Excel プロジェクトの次のコード ファイルがブックとテンプレートの両方のプロジェクトで自動的に作成されます。  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 プロジェクト内の `Globals` クラスを使用して、それぞれのクラスの外部から `ThisWorkbook`、`Sheet1`、`Sheet2`、または `Sheet3` にアクセスすることができます。 詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。 次の例では、<xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>メソッドの`Sheet1`のいずれかに、コードを配置するかどうかに関係なく、 `Sheet` *n*クラスまたは`ThisWorkbook`クラスです。  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Excel ドキュメントのデータは高度に構造化されているため、オブジェクト モデルは階層的で単純です。 Excel では対話が可能な何百ものオブジェクトを提供していますが、最初にオブジェクト モデルを使い始めるときは、使用可能なオブジェクトの非常に小さなサブセットに重点を置くと良いでしょう。 このようなオブジェクトには次の 4 つがあります。  
  
-   アプリケーション  
  
-   ブック  
  
-   ワークシート  
  
-   範囲  
  
 Excel の作業の多くはこれら 4 つのオブジェクトとそのメンバーを中心に行われます。  
  
### <a name="application-object"></a>アプリケーション オブジェクト  
 Excel の <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、Excel のアプリケーション自体を表します。 <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、実行中のアプリケーション、そのインスタンスに適用されるオプション、そのインスタンス内で開いている現在のユーザー オブジェクトに関する多くの情報を公開します。  
  
> [!NOTE]  
>  設定を適用しないで、<xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A>のプロパティ、<xref:Microsoft.Office.Interop.Excel.Application>を Excel のオブジェクト**false**です。 このプロパティを false に設定すると、ホスト コントロールのイベントを含む、すべてのイベントが Excel で発生しなくなります。  
  
### <a name="workbook-object"></a>ブックのオブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトは、Excel アプリケーション内の 1 つのブックを表します。  
  
 Visual Studio の Office 開発ツールは、<xref:Microsoft.Office.Tools.Excel.Workbook> 型を提供することにより、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトを拡張します。 この型により、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトのすべての機能にアクセスできるようになります。 詳細については、「 [Workbook Host Item](../vsto/workbook-host-item.md)」を参照してください。  
  
### <a name="worksheet-object"></a>ワークシート オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトは <xref:Microsoft.Office.Interop.Excel.Worksheets> コレクションのメンバーです。 <xref:Microsoft.Office.Interop.Excel.Worksheet> のプロパティ、メソッド、およびイベントの多くは、<xref:Microsoft.Office.Interop.Excel.Application> または <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトによって提供されるメンバーと同一か類似しています。  
  
 Excel は、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトのプロパティとして <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを提供します。 <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの各メンバーは、<xref:Microsoft.Office.Interop.Excel.Worksheet> または <xref:Microsoft.Office.Interop.Excel.Chart> オブジェクトのどちらかです。  
  
 Visual Studio の Office 開発ツールは、<xref:Microsoft.Office.Tools.Excel.Worksheet> 型を提供することにより、<xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトを拡張します。 この型は <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトのすべての機能にアクセスできるだけでなく、マネージ コントロールをホストし、新しいイベントを処理する機能などの新機能にもアクセスできます。 詳細については、「 [Worksheet Host Item](../vsto/worksheet-host-item.md)」を参照してください。  
  
### <a name="range-object"></a>Range オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトは、Excel アプリケーション内で特に使用されるオブジェクトです。 Excel 内で任意の領域を操作するには、その領域を <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトとして表し、その範囲のメソッドとプロパティを作業する必要があります。 <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトは、セル、行、列、セルの 1 つ以上のブロックを含むセルの選択を表します。連続する場合もしない場合もあり、セルのグループが複数のシートにわたっている場合もあります。  
  
 Visual Studio は <xref:Microsoft.Office.Tools.Excel.NamedRange> および <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 型を提供することで <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトを拡張します。 これらの型は <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトとほぼ同じ機能を含むだけでなく、データ バインド機能や新しいイベントなどの新機能も含んでいます。 詳細については、次を参照してください。 [NamedRange コントロール](../vsto/namedrange-control.md)と[XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)です。  
  
##  <a name="ExcelOMDocumentation"></a> Excel オブジェクト モデル ドキュメントの使用  
 Excel オブジェクト モデルに関する詳細については、Excel プライマリ相互運用機能アセンブリ (PIA) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### <a name="primary-interop-assembly-reference"></a>プライマリ相互運用機能アセンブリのリファレンス  
 Excel PIA のリファレンス ドキュメントは、Excel のプライマリ相互運用機能アセンブリの種類について説明しています。 このドキュメントは、次の場所から使用可能な: [Excel 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)です。  
  
 PIA のイベントの実装方法、PIA のクラスとインターフェイスの違いなど、Excel PIA の設計の詳細については「[クラスの概要と、Office プライマリ相互運用機能アセンブリインターフェイス](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>VBA オブジェクト モデルのリファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される Excel オブジェクト モデルについて説明しています。 詳細については、次を参照してください。 [Excel 2010 オブジェクト モデル リファレンス](http://go.microsoft.com/fwlink/?LinkId=199768)です。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Excel PIA の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内のワークシート オブジェクトに対応しています。、 <xref:Microsoft.Office.Interop.Excel.Worksheet> 、Excel pia のオブジェクト。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Excel プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
### <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Excel ソリューション](../vsto/excel-solutions.md)|Microsoft Office Excel でドキュメント レベルのカスタマイズと VSTO アドインを作成する方法について説明します。|  
|[範囲の操作](../vsto/working-with-ranges.md)|範囲を使用して一般的なタスクを実行する方法を示す例を提供します。|  
|[ワークシートの操作](../vsto/working-with-worksheets.md)|ワークシートを使用して一般的なタスクを実行する方法を示す例を提供します。|  
|[ブックの操作](../vsto/working-with-workbooks.md)|ブックを使用して一般的なタスクを実行する方法を示す例を提供します。|  
  
  