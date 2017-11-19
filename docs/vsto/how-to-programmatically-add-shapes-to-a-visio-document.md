---
title: "方法: プログラムによって Visio 図面に図形を追加 |Microsoft ドキュメント"
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
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39843950cb592aa40b11e098f62018a4dc6e2983
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>方法: プログラムによって Visio 図面に図形を追加する
  ステンシルからマスターを取得し、図形をアクティブ ページにドロップすると、Microsoft Office Visio 図面に図形を追加できます。  
  
 詳しくは、 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) メソッド、 [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) プロパティ、 [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) メソッドの VBA リファレンス ドキュメントをご覧ください。  
  
## <a name="adding-shapes-to-a-visio-document"></a>Visio 図面への図形の追加  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>Visio 図面に図形を追加するには  
  
-   ドキュメントをアクティブにして、Documents.Masters コレクションからマスターを取得し、アクティブなドキュメントに図形をドロップします。 インデックスまたはマスターの名前を使用して、マスターを取得できます。  
  
     次のコード例は、空の Visio 図面を作成し、 **[基本図形]** ステンシルをドッキングした状態で図面を開きます。 次に、このコードはいくつかの図形を取得し、それらをアクティブ ページにドロップします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Visio 図形の操作](../vsto/working-with-visio-shapes.md)   
 [方法: Visio 図面の図形をプログラムによってコピーして貼り付ける](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  