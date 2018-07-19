---
title: '方法: プログラムによって Visio 図面を開く'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257853"
---
# <a name="how-to-programmatically-open-visio-documents"></a>方法: プログラムによって Visio 図面を開く
  既存の Microsoft Office Visio 図面を開くための 2 つの方法があります: オープン、OpenEx します。 メソッドは、図面を開く方法を呼び出し元が指定できる引数を提供する点を除いて、Open メソッドと同じです。  
  
 オブジェクト モデルの詳細については、 [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) メソッドと [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="open-a-visio-document"></a>Visio 図面を開く  
  
### <a name="to-open-a-visio-document"></a>Visio 図面を開くには  
  
-   呼び出す、`Microsoft.Office.Interop.Visio.Documents.Open`メソッドを Visio 図面の完全修飾パスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>指定された引数で Visio 図面を開く  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>読み取り専用およびドッキングとして Visio 図面を開くには  
  
-   呼び出す、`Microsoft.Office.Interop.Visio.Documents.OpenEx`メソッドが、Visio 図面の完全修飾パスを指定し、引数を使用する: このケース、ドッキング、読み取り専用にします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 このコード例で必要な要素は次のとおりです。  
  
-   という名前の Visio 図面`myDrawing.vsd`という名前のディレクトリである必要があります`Test`で、 *My Documents*フォルダー (Windows XP 以前) または*ドキュメント*フォルダー (Windows Vista)。  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷します。](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  