---
title: '方法: プログラムによってコピーして、Visio 図面に図形を貼り付けます'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fe02a88c5213fd67e26dc545af4b18a64473c754
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865179"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>方法: プログラムによってコピーして、Visio 図面に図形を貼り付けます
  プログラムを使用してドキュメントの 1 つのページ上の図形をコピーし、同じドキュメント内の新しいページに貼り付けることができます。 貼り付け先として、既定の場所 (アクティブ ウィンドウの中央)、または元のページと同じ座標位置を選択できます。  
  
## <a name="copy-and-paste-shapes"></a>コピーして、図形を貼り付けます  
 オブジェクト モデルの詳細については、 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval)、 [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)、および [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) メソッドと [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) フラグの VBA リファレンス ドキュメントを参照してください。  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>別のページの中央に図形をコピーするには  
  
-   次の例では、最初のページの図形をコピーし、2 番目のページの中央に貼り付ける方法を示します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>図形と同じ位置にコピーして貼り付ける  
 オブジェクト モデルの詳細については、 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval)、 [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)、および [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) メソッドと [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) フラグの VBA リファレンス ドキュメントを参照してください。  
  
 貼り付けた情報の形式を制御し、(必要に応じて) ソース ファイル (たとえば、Microsoft Office Word ドキュメントなど) へのリンクを確立する必要がある場合は、PasteSpecial メソッドを使用します。  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>図形と図形の位置を別のページにコピーするには  
  
-   次の例では、最初のページの図形をコピーし、2 番目のページの同じ座標位置に貼り付ける方法を示します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Visio 図形を操作します。](../vsto/working-with-visio-shapes.md)   
 [方法: プログラムによって Visio 図面に図形を追加します。](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
