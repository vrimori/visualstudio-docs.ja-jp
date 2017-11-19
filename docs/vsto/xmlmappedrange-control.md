---
title: "XmlMappedRange コントロール |Microsoft ドキュメント"
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
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 391964152c48601b11b10ce6d8001d2d303a9a01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange コントロール
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールは、繰り返しのないスキーマ要素は、Microsoft Office Excel のセルに対応しているときにのみ作成される範囲です。 たとえば、ときに、`maxOccurs`スキーマ要素の属性が 1 に等しい。 Visual Studio では、マップされた XML の範囲が作成された後は、Excel オブジェクト モデルを走査する必要なく、直接に対してプログラミングできます。 のみを削除することができます、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>要素のマッピングが削除されたときに Excel 内で制御します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: を使用して XML マッピング Excel で?](http://go.microsoft.com/fwlink/?LinkID=130288)です。  
  
## <a name="binding-data-to-the-control"></a>コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールは単一のデータ フィールド (単純データ バインディング) へのバインドをサポートします。 <xref:Microsoft.Office.Tools.Excel.ListObject>コントロールは、複合データ バインディングをサポートし、繰り返されるスキーマ要素がセル上にマップされている場合は自動的に作成します。 詳細については、「 [ListObject Control](../vsto/listobject-control.md)」を参照してください。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>を使用してデータ ソースにコントロールがバインドされている、<xref:System.Windows.Forms.Control.DataBindings%2A>プロパティです。 ときに、 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Visual Studio は自動的にマップされているセルに、データからデータ セットを生成し、コントロールをデータ セットをバインドしますが、ワークシートのセルに追加します。 既定のデータ バインディング プロパティ、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>は<xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>します。  
  
 バインドされたデータ セット内のデータが任意のメカニズムにより更新された場合、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールが変更を反映します。  
  
## <a name="formatting"></a>書式設定  
 同じ書式を適用することができます、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールに適用可能な<xref:Microsoft.Office.Interop.Excel.Range>です。 これには、罫線、フォント、番号形式、スタイルが含まれます。  
  
## <a name="events"></a>イベント  
 利用可能なイベント、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールは。  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法: ワークシートに XMLMappedRange コントロールを追加します。](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法: Visual Studio 内のワークシートにスキーマのマッピング](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  