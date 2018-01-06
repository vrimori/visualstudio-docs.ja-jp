---
title: "方法: プログラムによって Visio 図面を開く |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b2a6c395ed6dbfb8265ac131dd4318b590bf92e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-visio-documents"></a>方法: プログラムによって Visio 図面を開く
  既存の Microsoft Office Visio 図面を開くための 2 つの方法があります。 Open および OpenEx です。 呼び出し元を指定できる引数はドキュメントを開く方法を提供する点を除いて、メソッドは、開いているメソッドと同じです。  
  
 オブジェクト モデルの詳細については、 [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) メソッドと [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="opening-a-visio-document"></a>Visio 図面を開く  
  
#### <a name="to-open-a-visio-document"></a>Visio 図面を開くには  
  
-   Microsoft.Office.Interop.Visio.Documents.Open メソッドを呼び出し、Visio 図面の完全修飾パスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>引数を指定して Visio 図面を開く  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>読み取り専用およびドッキングとして Visio 図面を開くには  
  
-   Microsoft.Office.Interop.Visio.Documents.OpenEx メソッドを呼び出して、Visio 図面の完全修飾パスを指定および使用する引数を含める: このユース ケース、ドッキングされた状態、および読み取り専用にします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   [マイ ドキュメント] フォルダー (Windows XP 以前の場合) または [ドキュメント] フォルダー (Windows Vista の場合) 内の `myDrawing.vsd` というディレクトリにある `Test` という名前の Visio 図面。  
  
## <a name="see-also"></a>参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成します。](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  