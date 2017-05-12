---
title: "拡張オブジェクトによる Excel の自動化"
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
  - "Excel [Visual Studio での Office 開発]、自動化"
  - "オートメーション [Visual Studio での Office 開発]、Excel"
  - "ホスト コントロール、Excel"
  - "Excel [Visual Studio での Office 開発]、ホスト コントロール"
  - "拡張オブジェクト [Visual Studio での Office 開発]、Excel"
  - "ホスト コントロール [Visual Studio での Office 開発]、Excel"
  - "自動化 (Excel を)"
  - "ホスト コントロール [Visual Studio での Office 開発]、Excel"
  - "コントロール [Visual Studio での Office 開発]、Excel ホスト コントロール"
ms.assetid: 3ed99480-234d-46b1-b91c-226018bd3faf
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 拡張オブジェクトによる Excel の自動化
  Visual Studio で Excel ソリューションを作成する場合、ソリューションで*ホスト項目*および*ホスト コントロール*を使用できます。 これらのオブジェクトは、Excel オブジェクト モデル \(つまり Excel のプライマリ相互運用機能アセンブリによって公開されるオブジェクト モデル\) 内にある、<xref:Microsoft.Office.Interop.Excel.Worksheet> や <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトなど、よく使用される特定のオブジェクトを拡張したオブジェクトです。 これらの拡張オブジェクトは、基になる Excel オブジェクトと同じように動作しますが、新しいイベントやデータ バインディング機能など、基のオブジェクトにはない機能が追加されています。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ホスト項目とホスト コントロールは、VSTO アドインとドキュメント レベルのカスタマイズの両方で使用できます。ただし、使用できるコンテキストはそれおぞれのソリューションの種類で異なります。 詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
## Excel ホスト項目  
 Excel プロジェクトでは、次のホスト項目にアクセスできます。  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>。  このホスト項目はプロジェクトのワークシートを表します。 また、ホスト コントロールや Windows フォーム コントロールなどのマネージ コントロールを格納するコンテナーの役割も果たし、画面のコントロールに関する情報を保持します。 詳細については、「[Worksheet ホスト項目](../vsto/worksheet-host-item.md)」を参照してください。  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>。 このホスト項目はプロジェクトのブックを表し、ブック内のすべてのワークシートで共有されるコンポーネントを格納するコンテナーとして動作します。 詳細については、「[Workbook ホスト項目](../vsto/workbook-host-item.md)」を参照してください。  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>。 このホスト項目はグラフのみを含む Excel ワークシートを表し、イベントを公開します。  
  
     Microsoft Office Excel のドキュメント レベルのカスタマイズ プロジェクトで、デザイン時に新しいシートとしてグラフ シートを追加した場合、Visual Studio によって自動的に <xref:Microsoft.Office.Tools.Excel.ChartSheet> ホスト項目が作成されます。  
  
     <xref:Microsoft.Office.Tools.Excel.ChartSheet> ホスト項目は Excel のワークシートですが、このグラフ シートにはコントロールを追加できません。 グラフを含むワークシート上に他のコントロールを追加する場合は、グラフ シートを使用しないでください。 代わりに、<xref:Microsoft.Office.Tools.Excel.Chart> ホスト コントロールを使用して、ワークシート上の埋め込みオブジェクトとしてグラフを配置できます。 詳細については、「[Chart コントロール](../vsto/chart-control.md)」を参照してください。  
  
## Excel ホスト コントロール  
 Excel には、ブックやワークシートの作成、整理、および自動化に役立つホスト コントロールがいくつかあります。 これらのホスト コントロールには、Excel のネイティブ オブジェクト モデルの対応するコントロールにはないイベントやデータ バインディング機能が用意されています。  
  
 Excel プロジェクトで使用できるホストのコントロールの詳細については、次のトピックを参照してください。  
  
-   [Chart コントロール](../vsto/chart-control.md)  
  
-   [ListObject コントロール](../vsto/listobject-control.md)  
  
-   [NamedRange コントロール](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)  
  
## 参照  
 [方法 : ListObject コントロールにデータを読み込む](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [方法 : ワークシートに Chart コントロールを追加する](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [方法 : ワークシートに ListObject コントロールを追加する](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法 : ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法 : ワークシートに XMLMappedRange コントロールを追加する](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [方法 : NamedRange コントロールのサイズを変更する](../vsto/how-to-resize-namedrange-controls.md)   
 [方法 : ListObject コントロールのサイズを変更する](../vsto/how-to-resize-listobject-controls.md)   
 [方法 : ListObject コントロールに新規行が追加された場合にデータを検証する](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [方法 : データに ListObject 列を割り当てる](../vsto/how-to-map-listobject-columns-to-data.md)   
 [チュートリアル : NamedRange コントロールのイベントのプログラミング  
](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  