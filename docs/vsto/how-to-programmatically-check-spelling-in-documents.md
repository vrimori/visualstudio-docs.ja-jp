---
title: "方法: プログラムによって文書でスペル チェック |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 357e92235f474392c3bdbe1ac1f19af8c9c1538a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>方法: プログラムによって文書でスペル チェックを行う
  ドキュメント内のスペルを確認するには、使用、<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>メソッドです。 このメソッドは、指定されたパラメーターのスペルが正しいかどうかを示すブール値を返します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>スペル チェックを行うと、メッセージ ボックスに結果を表示するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>メソッドのスペルを確認するテキストの範囲を渡します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによってを定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  