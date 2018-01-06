---
title: "拡張オブジェクトを使用して Excel の自動化 |Microsoft ドキュメント"
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
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
ms.assetid: 3ed99480-234d-46b1-b91c-226018bd3faf
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f8342db2cc5803aaed31a7bda0cc8d8b6ae15e83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="automating-excel-by-using-extended-objects"></a>拡張オブジェクトによる Excel の自動化
  Visual Studio で Excel ソリューションを作成する場合、ソリューションで *ホスト項目* および *ホスト コントロール*を使用できます。 これらのオブジェクトは、Excel オブジェクト モデル (つまり Excel のプライマリ相互運用機能アセンブリによって公開されるオブジェクト モデル) 内にある、 <xref:Microsoft.Office.Interop.Excel.Worksheet> や <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトなど、よく使用される特定のオブジェクトを拡張したオブジェクトです。 これらの拡張オブジェクトは、基になる Excel オブジェクトと同じように動作しますが、新しいイベントやデータ バインディング機能など、基のオブジェクトにはない機能が追加されています。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ホスト項目とホスト コントロールは、VSTO アドインとドキュメント レベルのカスタマイズの両方で使用できます。ただし、使用できるコンテキストはそれおぞれのソリューションの種類で異なります。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
## <a name="excel-host-items"></a>Excel ホスト項目  
 Excel プロジェクトでは、次のホスト項目にアクセスできます。  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>。 このホスト項目はプロジェクトのワークシートを表します。 また、ホスト コントロールや Windows フォーム コントロールなどのマネージ コントロールを格納するコンテナーの役割も果たし、画面のコントロールに関する情報を保持します。 詳細については、「 [Worksheet Host Item](../vsto/worksheet-host-item.md)」を参照してください。  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>。 このホスト項目はプロジェクトのブックを表し、ブック内のすべてのワークシートで共有されるコンポーネントを格納するコンテナーとして動作します。 詳細については、「 [Workbook Host Item](../vsto/workbook-host-item.md)」を参照してください。  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>。 このホスト項目はグラフのみを含む Excel ワークシートを表し、イベントを公開します。  
  
     Microsoft Office Excel のドキュメント レベルのカスタマイズ プロジェクトで、デザイン時に新しいシートとしてグラフ シートを追加した場合、Visual Studio によって自動的に <xref:Microsoft.Office.Tools.Excel.ChartSheet> ホスト項目が作成されます。  
  
     <xref:Microsoft.Office.Tools.Excel.ChartSheet> ホスト項目は Excel のワークシートですが、このグラフ シートにはコントロールを追加できません。 グラフを含むワークシート上に他のコントロールを追加する場合は、グラフ シートを使用しないでください。 代わりに、 <xref:Microsoft.Office.Tools.Excel.Chart> ホスト コントロールを使用して、ワークシート上の埋め込みオブジェクトとしてグラフを配置できます。 詳細については、「 [Chart Control](../vsto/chart-control.md)」を参照してください。  
  
## <a name="excel-host-controls"></a>Excel ホスト コントロール  
 Excel には、ブックやワークシートの作成、整理、および自動化に役立つホスト コントロールがいくつかあります。 これらのホスト コントロールには、Excel のネイティブ オブジェクト モデルの対応するコントロールにはないイベントやデータ バインディング機能が用意されています。  
  
 Excel プロジェクトで使用できるホストのコントロールの詳細については、次のトピックを参照してください。  
  
-   [Chart Control](../vsto/chart-control.md)  
  
-   [ListObject コントロール](../vsto/listobject-control.md)  
  
-   [NamedRange コントロール](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)  
  
## <a name="see-also"></a>参照  
 [方法: ListObject コントロールにデータを入力](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [方法: ワークシートに Chart コントロールを追加します。](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [方法: ワークシートに ListObject コントロールを追加します。](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法: ワークシートに XMLMappedRange コントロールを追加します。](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [方法: NamedRange コントロールのサイズを変更します。](../vsto/how-to-resize-namedrange-controls.md)   
 [方法: ListObject コントロールのサイズを変更します。](../vsto/how-to-resize-listobject-controls.md)   
 [方法: ListObject コントロールに新しい行が追加されたときにデータの検証](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [方法: データに ListObject 列をマップ](../vsto/how-to-map-listobject-columns-to-data.md)   
 [チュートリアル: NamedRange コントロールのイベントのプログラミング](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  