---
title: XmlMappedRange コントロール
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9cf21ceda64fe79996e05426a3379972c3c4be33
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673051"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange コントロール
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールが Microsoft Office Excel 内のセルに非繰り返しスキーマ要素がマップされている場合にのみ作成される範囲。 たとえば、ときに、`maxOccurs`スキーマ要素の属性が 1 に等しい。 Visual Studio には、XML が割り当てられた範囲が作成されたら、それに対して、Excel オブジェクト モデルを走査することがなく直接プログラミングできます。 のみを削除することができます、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>要素のマッピングが削除されると、Excel 内のコントロール。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [Excel で操作の使用の XML のマッピングを操作する方法でしょうか。](http://go.microsoft.com/fwlink/?LinkID=130288)します。  
  
## <a name="bind-data-to-the-control"></a>データをコントロールにバインドします。  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールは、1 つのデータ フィールド (単純データ バインディング) へのバインドをサポートしています。 <xref:Microsoft.Office.Tools.Excel.ListObject>コントロールは、複合データ バインディングをサポートしているし、繰り返されるスキーマ要素がセル上にマップされている場合は自動的に作成します。 詳細については、次を参照してください。 [ListObject コントロール](../vsto/listobject-control.md)します。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールを使用してデータ ソースにバインドする、<xref:System.Windows.Forms.Control.DataBindings%2A>プロパティ。 ときに、 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Visual Studio は、自動的に、マップされたセルのデータからデータ セットを生成し、そのデータ セットに、コントロールをバインドにワークシートのセルに追加されます。 既定のデータ バインディング プロパティ、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>は<xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>します。  
  
 バインドされたデータ セット内のデータが任意のメカニズムにより更新された場合、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールが変更を反映します。  
  
## <a name="formatting"></a>書式設定  
 同じ書式設定を適用することができます、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールに適用できる、<xref:Microsoft.Office.Interop.Excel.Range>します。 これには、罫線、フォント、番号形式、スタイルが含まれます。  
  
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
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法: ワークシートに XMLMappedRange コントロールを追加](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法: Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  