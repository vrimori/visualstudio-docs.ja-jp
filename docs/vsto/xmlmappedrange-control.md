---
title: "XmlMappedRange コントロール"
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
  - "XMLMappedRange コントロール"
  - "XMLMappedRange コントロール, データ バインド"
  - "XMLMappedRange コントロール, イベント"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# XmlMappedRange コントロール
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールは、非繰り返しスキーマ要素が Microsoft Office Excel のセルに割り当てられる場合にのみ作成される範囲です。  たとえば、スキーマ要素の `maxOccurs` 属性が 1 になる場合があります。  Visual Studio で XML が割り当てられた範囲が作成された後、この範囲は、Excel オブジェクト モデルを走査しなくても、コードで直接使用できます。  Excel 内で <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールを削除できるのは、要素の割り当てが解除されたときのみです。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[How Do I: Use XML Mapping in Excel? \(操作方法: Excel で XML マッピングを使用する\)](http://go.microsoft.com/fwlink/?LinkID=130288)」を参照してください。  
  
## コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールは、1 つのデータ フィールドへのバインディング \(単純データ バインディング\) をサポートします。  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは、複合データ バインディングをサポートし、セルに繰り返しスキーマ要素が割り当てられると自動的に作成されます。  詳細については、「[ListObject コントロール](../vsto/listobject-control.md)」を参照してください。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールは、<xref:System.Windows.Forms.Control.DataBindings%2A> プロパティを使用してデータ ソースにバインドされます。  ワークシートのセルに <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> が追加されると、割り当てられているセルのデータに基づいて Visual Studio によって自動的にデータ セットが生成され、コントロールがそのデータセットにバインドされます。  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> の既定のデータ バインディング プロパティは、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> です。  
  
 バインドされたデータセット内のデータがなんらかの機構をとおして更新された場合、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールはその変更を反映します。  
  
## 書式設定  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールには、<xref:Microsoft.Office.Interop.Excel.Range> に適用するのと同じ書式設定を適用できます。  これには、罫線、フォント、数値の形式、およびスタイルがあります。  
  
## イベント  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールで使用できるイベントは次のとおりです。  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## 参照  
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法 : ワークシートに XMLMappedRange コントロールを追加する](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法 : Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  