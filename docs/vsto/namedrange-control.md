---
title: NamedRange コントロール |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5273baec024da8eb339e8f3d12541fc6e98e97c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="namedrange-control"></a>NamedRange コントロール
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールは、一意の名前を持つ、イベントを公開する範囲です。このコントロールは、データにバインドすることができます。 詳細については、「 [Excel Object Model Overview](../vsto/excel-object-model-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>コントロールの作成  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを Microsoft Office Excel ワークシートに追加できます。  
  
 VSTO アドインでは実行時に <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをワークシートに追加できます。 詳細については、「 [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md)」を参照してください。  
  
> [!NOTE]  
>  既定では、動的に作成された名前付き範囲は、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、「 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールは、特定のシート上の範囲でしか構成できません。 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの名前には、すべてのシートに適用される相対名を使用できません。また、ブックの複数のワークシートにまたがる範囲 (3-D 範囲) で構成することもできません。  
  
## <a name="binding-data-to-the-control"></a>コントロールへのデータのバインド  
 名前付き範囲は多数のセルを使用できるため、複合データ バインディングで有力候補となりそうですが、範囲は単なるセルのコレクションでしかなく、データセットの特定の列に簡単にマップすることはできません。 したがって、 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがサポートするのは単純なデータ バインディングのみです。 複合データ バインディングには <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを使用できます。 詳細については、「 [ListObject Control](../vsto/listobject-control.md)」を参照してください。  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをデータ ソースにバインドするには、 <xref:System.Windows.Forms.Control.DataBindings%2A> プロパティを使用します。 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの既定のデータ バインディング プロパティは <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>です。  
  
 バインドされたデータセット内のデータが任意のメカニズムにより更新された場合に、 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールが変更を反映します。  
  
## <a name="formatting"></a>書式設定  
 <xref:Microsoft.Office.Interop.Excel.Range> に適用できる書式設定は、 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールに適用できます。 これには、罫線、フォント、番号形式、およびスタイルが含まれます。  
  
## <a name="renaming-the-control"></a>コントロールの名前変更  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> [ツールボックス] **から**コントロールをワークシートに追加すると、そのコントロールの名前が Visual Studio により自動的に生成されます。 名前は **[プロパティ]** ウィンドウで変更できます。  
  
## <a name="events"></a>イベント  
 次のイベントは <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールに対して利用できます。  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [方法: NamedRange コントロールのサイズを変更します。](../vsto/how-to-resize-namedrange-controls.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [チュートリアル: NamedRange コントロールのイベントのプログラミング](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  