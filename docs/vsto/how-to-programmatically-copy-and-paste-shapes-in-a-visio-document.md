---
title: '方法: プログラムによってコピーして、Visio 図面に図形を貼り付ける |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 488cda5519a211754498b50a88995de64a8ed366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>方法: Visio 図面の図形をプログラムによってコピーして貼り付ける
  プログラムを使用してドキュメントの 1 つのページ上の図形をコピーし、同じドキュメント内の新しいページに貼り付けることができます。 貼り付け先として、既定の場所 (アクティブ ウィンドウの中央)、または元のページと同じ座標位置を選択できます。  
  
## <a name="copying-and-pasting-shapes"></a>図形のコピーと貼り付け  
 オブジェクト モデルの詳細については、 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx)、 [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)、および [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) メソッドと [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) フラグの VBA リファレンス ドキュメントを参照してください。  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>別のページの中央に図形をコピーするには  
  
-   次の例では、最初のページの図形をコピーし、2 番目のページの中央に貼り付ける方法を示します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>図形をコピーし同じ位置に貼り付け  
 オブジェクト モデルの詳細については、 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx)、 [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)、および [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) メソッドと [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) フラグの VBA リファレンス ドキュメントを参照してください。  
  
 貼り付けた情報の形式を制御し、(必要に応じて) ソース ファイル (たとえば、Microsoft Office Word 文書) へのリンクを確立する必要がある場合は、PasteSpecial メソッドを使用します。  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>図形と図形の位置を別のページにコピーするには  
  
-   次の例では、最初のページの図形をコピーし、2 番目のページの同じ座標位置に貼り付ける方法を示します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Visio 図形の操作](../vsto/working-with-visio-shapes.md)   
 [方法: プログラムによって Visio 図面に図形を追加する](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  