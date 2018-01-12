---
title: "方法: プログラムによって Visio 図面を印刷 |Microsoft ドキュメント"
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
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2ce41f14758d1f34c3e8c31d2ec013fa24c27b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>方法: プログラムによって Visio 図面を印刷する
  Microsoft Office Visio 図面の全体または特定のページだけを印刷することができます。  
  
 印刷メソッドの詳細については、 [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) メソッドと [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="printing-a-visio-document"></a>Visio 図面を印刷する  
  
#### <a name="to-print-a-complete-document"></a>図面全体を印刷するには  
  
-   印刷する Microsoft.Office.Interop.Visio.Document オブジェクトの Microsoft.Office.Interop.Visio.Document.Print メソッドを呼び出します。  
  
     アクティブ文書を印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Visio 図面の特定のページを印刷する  
  
#### <a name="to-print-a-page-of-a-document"></a>特定のページの図面を印刷するには  
  
-   印刷する Microsoft.Office.Interop.Visio.Pages オブジェクトの Microsoft.Office.Interop.Visio.Pages.Print メソッドを呼び出します。  
  
     アクティブ文書の最初のページを印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成します。](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存する](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  