---
title: '方法: プログラムによって Visio 図面を閉じる'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e27b0a19005b7076629f2848f95c8cb5749c096f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673339"
---
# <a name="how-to-programmatically-close-visio-documents"></a>方法: プログラムによって Visio 図面を閉じる
  使用して、アクティブな Microsoft Office Visio 図面を閉じることができます、`Microsoft.Office.Interop.Visio.Document.Close`メソッド。  
  
 このメソッドの詳細については、 [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="close-the-active-document"></a>アクティブなドキュメントを閉じる  
  
### <a name="to-close-the-active-document"></a>作業中のドキュメントを閉じるには  
  
-   呼び出す、`Microsoft.Office.Interop.Visio.Document.Close`メソッドをアクティブなドキュメントを閉じます。  
  
     次のコード例を使用するで実行、 `ThisAddIn` Visio 用の VSTO アドイン プロジェクト内のクラス。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷します。](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  