---
title: Excel オブジェクト モデルの概要
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
ms.openlocfilehash: 8ca93cae45eed272b683275896efcf83229ca9a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880794"
---
# <a name="excel-object-model-overview"></a>Excel オブジェクト モデルの概要
  Microsoft Office Excel を使用するソリューションを開発するため、Excel オブジェクト モデルによって提供されるオブジェクトと対話することができます。 このトピックでは、特に重要なオブジェクトについて説明します。  
  
- <xref:Microsoft.Office.Interop.Excel.Application>  
  
- <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
- <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Interop.Excel.Range>  
  
  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
  オブジェクト モデルは、ユーザー インターフェイスに緊密に従います。 <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、アプリケーション全体を表し、それぞれの <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトには `Worksheet` オブジェクトのコレクションが含まれます。 つまり、セルを表す主要な概念は <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトになり、これにより個々のセルやセルのグループを使用できるようになります。  
  
  Visual Studio での Office プロジェクトを提供する Excel オブジェクト モデルだけでなく*ホスト項目*と*ホスト コントロール*Excel オブジェクト モデルの一部のオブジェクトを拡張します。 ホスト項目とホスト コントロールは、これらが拡張する Excel オブジェクトと同様に動作しますが、これ以外にデータ バインディング機能や他のイベントなどの追加機能もあります。 詳細については、次を参照してください。[拡張オブジェクトを使用して Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)と[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。  
  
  ここでは、Excel オブジェクト モデルの概念について簡単に説明します。 全体の Excel オブジェクト モデルの詳細を説明できます資料については、次を参照してください。 [Excel オブジェクト モデルのドキュメントを使用して、](#ExcelOMDocumentation)します。  
  
  ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i: を使用してイベント ハンドラーで、Excel 2007 アドイン?](http://go.microsoft.com/fwlink/?LinkID=130291)、および[How do i: を使用して図形をバブル チャートを作成するには。excel しますか](http://go.microsoft.com/fwlink/?LinkID=130313)。  
  
## <a name="access-objects-in-an-excel-project"></a>Excel プロジェクトでオブジェクトにアクセス  
 Excel の新しい VSTO アドイン プロジェクトを作成すると、Visual Studio は自動的に作成、 *ThisAddIn.vb*または*ThisAddIn.cs*コード ファイル。 `Me.Application` または `this.Application` を使用して、アプリケーション オブジェクトにアクセスすることができます。  
  
 Excel で新しいドキュメント レベルのプロジェクトを作成する場合は、新しい Excel ブックまたは Excel テンプレート プロジェクトを作成するオプションがあります。 Visual Studio によって新しい Excel プロジェクトの次のコード ファイルがブックとテンプレートの両方のプロジェクトで自動的に作成されます。  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 プロジェクト内の `Globals` クラスを使用して、それぞれのクラスの外部から `ThisWorkbook`、`Sheet1`、`Sheet2`、または `Sheet3` にアクセスすることができます。 詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)します。 次の例では、<xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>メソッドの`Sheet1`のいずれかで、コードを配置するかどうかに関係なく、 `Sheet` *n*クラスまたは`ThisWorkbook`クラス。  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Excel ドキュメントのデータは高度に構造化されているため、オブジェクト モデルは階層的で単純です。 Excel では、何百ものオブジェクトが、操作可能な場合がありますが、使用可能なオブジェクトの小さなサブセットに重点を置いた、最初に、オブジェクト モデルを取得できます。 このようなオブジェクトには次の 4 つがあります。  
  
- アプリケーション  
  
- ブック  
  
- ワークシート  
  
- 範囲  
  
  Excel の作業の多くはこれら 4 つのオブジェクトとそのメンバーを中心に行われます。  
  
### <a name="application-object"></a>Application オブジェクト  
 Excel の <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、Excel のアプリケーション自体を表します。 <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトは、実行中のアプリケーション、そのインスタンスに適用されるオプション、そのインスタンス内で開いている現在のユーザー オブジェクトに関する多くの情報を公開します。  
  
> [!NOTE]  
>  Excel の <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> オブジェクトの <xref:Microsoft.Office.Interop.Excel.Application> プロパティを **false**と呼ばれるオブジェクトを拡張します。 このプロパティを false に設定すると、ホスト コントロールのイベントを含む、すべてのイベントが Excel で発生しなくなります。  
  
### <a name="workbook-object"></a>Workbook オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトは、Excel アプリケーション内の 1 つのブックを表します。  
  
 Visual Studio の Office 開発ツールには、 <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトを拡張する <xref:Microsoft.Office.Tools.Excel.Workbook> 型が用意されています。 この型により、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトのすべての機能にアクセスできるようになります。 詳細については、次を参照してください。 [Workbook ホスト項目](../vsto/workbook-host-item.md)します。  
  
### <a name="worksheet-object"></a>Worksheet オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトは <xref:Microsoft.Office.Interop.Excel.Worksheets> コレクションのメンバーです。 <xref:Microsoft.Office.Interop.Excel.Worksheet> のプロパティ、メソッド、およびイベントの多くは、<xref:Microsoft.Office.Interop.Excel.Application> または <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトによって提供されるメンバーと同一か類似しています。  
  
 Excel は、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトのプロパティとして <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを提供します。 <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの各メンバーは、<xref:Microsoft.Office.Interop.Excel.Worksheet> または <xref:Microsoft.Office.Interop.Excel.Chart> オブジェクトのどちらかです。  
  
 Visual Studio の Office 開発ツールは、<xref:Microsoft.Office.Tools.Excel.Worksheet> 型を提供することにより、<xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトを拡張します。 この型は <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトのすべての機能にアクセスできるだけでなく、マネージド コントロールをホストし、新しいイベントを処理する機能などの新機能にもアクセスできます。 詳細については、次を参照してください。 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)します。  
  
### <a name="range-object"></a>Range オブジェクト  
 <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトは、Excel アプリケーション内で特に使用されるオブジェクトです。 Excel 内で任意の領域を操作するには、その領域を <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトとして表し、その範囲のメソッドとプロパティを作業する必要があります。 <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトは、セル、行、列、セルの 1 つ以上のブロックを含むセルの選択を表します。連続する場合もしない場合もあり、セルのグループが複数のシートにわたっている場合もあります。  
  
 Visual Studio は <xref:Microsoft.Office.Tools.Excel.NamedRange> および <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 型を提供することで <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトを拡張します。 これらの型は <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトとほぼ同じ機能を含むだけでなく、データ バインド機能や新しいイベントなどの新機能も含んでいます。 詳細については、次を参照してください。 [NamedRange コントロール](../vsto/namedrange-control.md)と[XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)します。  
  
##  <a name="ExcelOMDocumentation"></a> Excel オブジェクト モデル ドキュメントを使用します。  
 Excel オブジェクト モデルに関する詳細については、Excel プライマリ相互運用機能アセンブリ (PIA) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### <a name="primary-interop-assembly-reference"></a>プライマリ相互運用機能アセンブリのリファレンス  
 Excel PIA のリファレンス ドキュメントは、Excel のプライマリ相互運用機能アセンブリの種類について説明しています。 このドキュメントは、次の場所から使用可能な: [Excel 2010 プライマリ相互運用機能アセンブリ リファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)します。  
  
 PIA のイベントの実装方法、PIA のクラスとインターフェイスの違いなど、Excel PIA の設計に関する詳細を参照してください[Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)。  
  
### <a name="vba-object-model-reference"></a>VBA オブジェクト モデル リファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される Excel オブジェクト モデルについて説明しています。 詳細については、次を参照してください。 [Excel 2010 オブジェクト モデル リファレンス](http://go.microsoft.com/fwlink/?LinkId=199768)します。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Excel PIA の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内のワークシート オブジェクトの対応する、 <xref:Microsoft.Office.Interop.Excel.Worksheet> Excel pia オブジェクト。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Excel プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
### <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Excel ソリューション](../vsto/excel-solutions.md)|Microsoft Office Excel でドキュメント レベルのカスタマイズと VSTO アドインを作成する方法について説明します。|  
|[範囲を操作します。](../vsto/working-with-ranges.md)|範囲を使用して一般的なタスクを実行する方法を示す例を提供します。|  
|[ワークシートを操作します。](../vsto/working-with-worksheets.md)|ワークシートを使用して一般的なタスクを実行する方法を示す例を提供します。|  
|[ブックを操作します。](../vsto/working-with-workbooks.md)|ブックを使用して一般的なタスクを実行する方法を示す例を提供します。|  
  
  