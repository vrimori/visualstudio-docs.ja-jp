---
title: "方法: プログラムによってドキュメントのプロパティを Word の表を作成 |Microsoft ドキュメント"
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
- document properties, inserting in Word tables
- documents [Office development in Visual Studio], document properties
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b305196b9dd05ebf411c4c68e869f5c9c5cbffc5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-populate-word-tables-with-document-properties"></a>方法: プログラムによって Document プロパティを Word の表に読み込む
  次の例ではドキュメントの先頭に Microsoft Office Word の表を作成し、ホスト ドキュメントのプロパティのデータをそこに読み込みます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="populating-tables-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズでの表データの読み込み  
  
#### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>表を作成し、ドキュメントのプロパティ データをそこに読み込むには  
  
1.  ドキュメントの先頭に、範囲を設定します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#90](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#90)]
     [!code-csharp[Trin_VstcoreWordAutomation#90](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#90)]  
  
2.  表のタイトルを挿入し、段落記号を含めます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#91](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#91)]
     [!code-csharp[Trin_VstcoreWordAutomation#91](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#91)]  
  
3.  ドキュメントの範囲に表を追加します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#92](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#92)]
     [!code-csharp[Trin_VstcoreWordAutomation#92](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#92)]  
  
4.  表の書式を設定し、スタイルを適用します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#93](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#93)]
     [!code-csharp[Trin_VstcoreWordAutomation#93](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#93)]  
  
5.  セルにドキュメントのプロパティを挿入します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#94](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#94)]
     [!code-csharp[Trin_VstcoreWordAutomation#94](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#94)]  
  
 次の例は、全手順を示しています。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
 [!code-vb[Trin_VstcoreWordAutomation#89](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#89)]
 [!code-csharp[Trin_VstcoreWordAutomation#89](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#89)]  
  
## <a name="populating-tables-in-a-vsto-add-in"></a>VSTO アドインでの表データの読み込み  
  
#### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>表を作成し、ドキュメントのプロパティ データをそこに読み込むには  
  
1.  ドキュメントの先頭に、範囲を設定します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#90](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#90)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#90](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#90)]  
  
2.  表のタイトルを挿入し、段落記号を含めます。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#91](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#91)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#91](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#91)]  
  
3.  ドキュメントの範囲に表を追加します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#92](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#92)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#92](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#92)]  
  
4.  表の書式を設定し、スタイルを適用します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#93](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#93)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#93](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#93)]  
  
5.  セルにドキュメントのプロパティを挿入します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#94](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#94)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#94](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#94)]  
  
 次の例は、全手順を示しています。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
 [!code-vb[Trin_VstcoreWordAutomationAddIn#89](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#89)]
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#89](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#89)]  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって Word の表を作成します。](../vsto/how-to-programmatically-create-word-tables.md)   
 [方法: プログラムによって Word の表のセルにテキストと書式を追加](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [方法: プログラムによって Word の表に行と列を追加](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  