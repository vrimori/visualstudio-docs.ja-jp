---
title: "方法: プログラムによって Word の表に行と列を追加 |Microsoft ドキュメント"
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
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bcad8104f5267f86c6538077f6f53abbac986d52
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>方法: プログラムによって Word の表に行と列を追加する
  Microsoft Office Word の表では、セルが行と列に編成されます。 表に行を追加するには、<xref:Microsoft.Office.Interop.Word.Rows> オブジェクトの <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> メソッドを使用し、列を追加するには <xref:Microsoft.Office.Interop.Word.Columns> オブジェクトの <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>ドキュメント レベルのカスタマイズの例  
 次のコード例はドキュメント レベルのカスタマイズで使用できます。 これらの例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。 これらの例は、カスタマイズに関連するドキュメントに、少なくとも 1 つの表が既にあることを前提としています。  
  
> [!IMPORTANT]  
>  このコードは、次のいずれかのプロジェクト テンプレートを使用して作成したプロジェクトでのみ実行されます。  
>   
>  -   Word 2013 ドキュメント  
> -   Word 2013 テンプレート  
> -   Word 2010 ドキュメント  
> -   Word 2010 テンプレート  
>   
>  どのその他の種類のプロジェクトでこのタスクを実行する場合への参照を追加する必要があります、 **Microsoft.Office.Interop.Word**アセンブリ、およびは、テーブルに行と列を追加するそのアセンブリからクラスを使用する必要があります。 詳細については、次を参照してください。[する方法: ターゲット Office アプリケーション プライマリ相互運用機能アセンブリを利用して](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)と[Word 2010 プライマリ相互運用機能アセンブリ リファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)です。  
  
#### <a name="to-add-a-row-to-a-table"></a>表に行を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> メソッドを使用して表に行を追加します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>表に列を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> メソッドを使用し、次に <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> メソッドを使用してすべての列を同じ幅にします。  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>VSTO アドインの例  
 次のコード例は VSTO アドインで使用できます。 これらの例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。 これらの例は、作業中のドキュメントに少なくとも 1 つの表が既にあることを想定しています。  
  
> [!IMPORTANT]  
>  このコードは、Word VSTO アドイン テンプレートを使用して作成したプロジェクトでのみ実行されます。  
>   
>  どのその他の種類のプロジェクトでこのタスクを実行する場合への参照を追加する必要があります、 **Microsoft.Office.Interop.Word**アセンブリ、およびは、テーブルに行と列を追加するそのアセンブリからクラスを使用する必要があります。 詳細については、次を参照してください。[する方法: ターゲット Office アプリケーション プライマリ相互運用機能アセンブリを利用して](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)と[Word 2010 プライマリ相互運用機能アセンブリ リファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)です。  
  
#### <a name="to-add-a-row-to-a-table"></a>表に行を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> メソッドを使用して表に行を追加します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>表に列を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> メソッドを使用し、次に <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> メソッドを使用してすべての列を同じ幅にします。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって Word の表を作成します。](../vsto/how-to-programmatically-create-word-tables.md)   
 [方法: プログラムによって Word の表のセルにテキストと書式を追加](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [方法: プログラムによって Document プロパティを Word の表に読み込む](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  