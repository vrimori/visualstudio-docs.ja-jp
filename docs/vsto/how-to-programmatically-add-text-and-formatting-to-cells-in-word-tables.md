---
title: '方法: プログラムによって Word の表のセルにテキストと書式を追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1bbebc1dd1173250ef6c4328916e1cee66b371c4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867235"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>方法: プログラムによって Word の表のセルにテキストと書式を追加します。
  表はセルの集まりで構成されます。 個々の <xref:Microsoft.Office.Interop.Word.Cell> オブジェクトが表内の 1 つのセルを表します。 各セルは、表内の場所を指定して参照します。 次の例では、表の最初の行の最初の列のセルを参照し、そのセルにテキストを追加して、書式を適用します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-add-text-and-formatting-to-cells"></a>セルにテキストと書式設定を追加するには  
  
1.  表内の場所を指定してセルを参照し、そのセルにテキストを追加して書式を適用します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     次のコード例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって Word の表を作成します。](../vsto/how-to-programmatically-create-word-tables.md)   
 [方法: プログラムによって Word の表に行と列を追加します。](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [方法: プログラムによって document プロパティを Word の表に読み込む](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
