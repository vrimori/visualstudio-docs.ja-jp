---
title: "方法: プログラムによって Visio 図面を閉じる |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f59d4178e82cde6c476d9cab8d20a37dcb698262
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-close-visio-documents"></a>方法: プログラムによって Visio 図面を閉じる
  Microsoft.Office.Interop.Visio.Document.Close メソッドを使用して、アクティブな Microsoft Office Visio 図面を閉じることができます。  
  
 このメソッドの詳細については、 [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="closing-the-active-document"></a>作業中の文書を閉じる  
  
#### <a name="to-close-the-active-document"></a>作業中のドキュメントを閉じるには  
  
-   アクティブな文書を閉じる Microsoft.Office.Interop.Visio.Document.Close メソッドを呼び出します。  
  
     次のコード例を使用するには、Visio 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成します。](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  