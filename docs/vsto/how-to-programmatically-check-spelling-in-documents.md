---
title: '方法: プログラムによって文書でスペルをチェックします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19dc596851ba8ca8b2ea3ef50e7d151220354e3b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087764"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>方法: プログラムによって文書でスペルをチェックします。
  ドキュメント内のスペルを確認するには、使用、<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>メソッド。 このメソッドは、指定されたパラメーターのスペルが正しいかどうかを示すブール値を返します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>スペルを確認し、メッセージ ボックスに結果を表示するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>メソッドをさまざまなスペルをチェックするテキストを渡します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムで定義し、ドキュメントで範囲を選択します](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
